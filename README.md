# IQueryableEF - Include IQueryable include table 

Include tables into IQueryable object when you need to select the entities that EF you want to return.

        public async Task<IEnumerable<TEntity>> FindAsync(Expression<Func<TEntity, bool>> predicate, List<Expression<Func<TEntity, object>>> includes)
        {
            IQueryable<TEntity> query = DbContext.Set<TEntity>();

            foreach (Expression<Func<TEntity, object>> include in includes)
            {
                query = query.Include(include);
            }

            return await query.Where(predicate).ToListAsync();
        }
        
        
