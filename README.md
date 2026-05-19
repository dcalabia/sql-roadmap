<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SQL Roadmap</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=IBM+Plex+Sans:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0f1117;
  --bg2: #171a23;
  --bg3: #1e2130;
  --border: rgba(255,255,255,0.08);
  --border2: rgba(255,255,255,0.14);
  --text: #e8eaf0;
  --muted: #8b90a0;
  --accent1: #4a9eff;
  --accent2: #3ecf8e;
  --accent3: #ff7b54;
  --accent4: #a78bfa;
  --font: 'IBM Plex Sans', sans-serif;
  --mono: 'IBM Plex Mono', monospace;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: var(--font);
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
}

/* ── SETUP BANNER ── */
#setup-banner {
  background: #1a1200;
  border-bottom: 1px solid #5a3e00;
  padding: 10px 20px;
  font-size: 12px;
  color: #f0c060;
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}
#setup-banner a { color: #f0c060; }
#setup-banner.hidden { display: none; }
.setup-close {
  margin-left: auto;
  background: none;
  border: none;
  color: #f0c060;
  cursor: pointer;
  font-size: 16px;
}

/* ── TOP BAR ── */
.topbar {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 14px 24px;
  border-bottom: 1px solid var(--border);
  background: var(--bg2);
  position: sticky;
  top: 0;
  z-index: 50;
}
.logo {
  font-family: var(--mono);
  font-size: 14px;
  font-weight: 500;
  color: var(--accent1);
  letter-spacing: 0.04em;
}
.topbar-right {
  margin-left: auto;
  display: flex;
  align-items: center;
  gap: 10px;
}
.sync-status {
  font-size: 11px;
  color: var(--muted);
  font-family: var(--mono);
}
.sync-status.ok { color: var(--accent2); }
.sync-status.err { color: var(--accent3); }
.btn {
  font-family: var(--font);
  font-size: 12px;
  font-weight: 500;
  padding: 6px 14px;
  border-radius: 6px;
  cursor: pointer;
  border: 1px solid var(--border2);
  background: var(--bg3);
  color: var(--text);
  transition: background 0.15s;
}
.btn:hover { background: #2a2f42; }
.btn-primary {
  background: var(--accent1);
  color: #fff;
  border-color: var(--accent1);
}
.btn-primary:hover { background: #3a8eef; }
.btn-sm {
  padding: 4px 10px;
  font-size: 11px;
}

/* ── LAYOUT ── */
.layout {
  display: grid;
  grid-template-columns: 1fr;
  max-width: 760px;
  margin: 0 auto;
  padding: 28px 20px 80px;
  gap: 8px;
}

/* ── PROGRESS BAR ── */
.progress-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
}
.progress-label {
  font-size: 11px;
  font-family: var(--mono);
  color: var(--muted);
  white-space: nowrap;
}
.progress-bar-bg {
  flex: 1;
  height: 4px;
  background: var(--bg3);
  border-radius: 2px;
  overflow: hidden;
}
.progress-bar-fill {
  height: 100%;
  background: var(--accent2);
  border-radius: 2px;
  transition: width 0.4s ease;
}

/* ── CHAPTER ── */
.chapter {
  border: 1px solid var(--border);
  border-radius: 10px;
  overflow: hidden;
  background: var(--bg2);
  transition: border-color 0.15s;
}
.chapter:hover { border-color: var(--border2); }
.chapter-header {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 13px 16px;
  cursor: pointer;
  user-select: none;
}
.ch-num {
  font-family: var(--mono);
  font-size: 10px;
  color: var(--muted);
  min-width: 26px;
}
.ch-dot {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  flex-shrink: 0;
}
.ch-title {
  font-size: 13px;
  font-weight: 500;
  flex: 1;
}
.ch-count {
  font-size: 10px;
  font-family: var(--mono);
  color: var(--muted);
  background: var(--bg3);
  padding: 2px 7px;
  border-radius: 20px;
}
.ch-arrow {
  font-size: 11px;
  color: var(--muted);
  transition: transform 0.2s;
}
.chapter.open .ch-arrow { transform: rotate(90deg); }

.subtopics {
  display: none;
  border-top: 1px solid var(--border);
}
.chapter.open .subtopics { display: block; }

.subtopic {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 9px 16px 9px 56px;
  cursor: pointer;
  border-bottom: 1px solid var(--border);
  transition: background 0.1s;
}
.subtopic:last-child { border-bottom: none; }
.subtopic:hover { background: var(--bg3); }
.subtopic-label {
  flex: 1;
  font-size: 12px;
  color: var(--muted);
}
.subtopic:hover .subtopic-label { color: var(--text); }
.note-dot {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: var(--accent1);
  opacity: 0;
  flex-shrink: 0;
}
.subtopic.has-note .note-dot { opacity: 1; }
.subtopic-meta {
  font-size: 10px;
  font-family: var(--mono);
  color: var(--muted);
  opacity: 0;
}
.subtopic.has-note .subtopic-meta { opacity: 0.6; }

/* ── NOTES PANEL ── */
.overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.5);
  z-index: 100;
}
.overlay.open { display: block; }

.panel {
  position: fixed;
  right: 0; top: 0; bottom: 0;
  width: 420px;
  max-width: 100vw;
  background: var(--bg2);
  border-left: 1px solid var(--border2);
  z-index: 101;
  display: flex;
  flex-direction: column;
  transform: translateX(100%);
  transition: transform 0.25s ease;
}
.panel.open { transform: translateX(0); }

.panel-header {
  padding: 16px 20px;
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: flex-start;
  gap: 12px;
}
.panel-close {
  background: none;
  border: none;
  cursor: pointer;
  color: var(--muted);
  font-size: 18px;
  line-height: 1;
  padding: 2px;
  margin-top: 1px;
}
.panel-close:hover { color: var(--text); }
.panel-titles { flex: 1; }
.panel-title {
  font-size: 14px;
  font-weight: 500;
  color: var(--text);
  line-height: 1.4;
}
.panel-chapter {
  font-size: 11px;
  font-family: var(--mono);
  color: var(--muted);
  margin-top: 3px;
}

.panel-body {
  flex: 1;
  display: flex;
  flex-direction: column;
  padding: 16px 20px;
  gap: 10px;
  overflow: hidden;
}
.notes-label {
  font-size: 10px;
  font-family: var(--mono);
  color: var(--muted);
  letter-spacing: 0.06em;
  text-transform: uppercase;
}
textarea#notesText {
  flex: 1;
  font-family: var(--mono);
  font-size: 12px;
  line-height: 1.7;
  color: var(--text);
  background: var(--bg3);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 12px 14px;
  resize: none;
  outline: none;
}
textarea#notesText:focus { border-color: var(--border2); }
textarea#notesText::placeholder { color: var(--muted); opacity: 0.5; }

.panel-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-bottom: 4px;
}
.save-hint {
  font-size: 11px;
  font-family: var(--mono);
  color: var(--muted);
}
.save-ok { color: var(--accent2); }

/* ── SETUP MODAL ── */
.modal-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.7);
  z-index: 200;
  align-items: center;
  justify-content: center;
  padding: 20px;
}
.modal-overlay.open { display: flex; }
.modal {
  background: var(--bg2);
  border: 1px solid var(--border2);
  border-radius: 12px;
  width: 100%;
  max-width: 560px;
  max-height: 90vh;
  overflow-y: auto;
  padding: 28px;
}
.modal h2 {
  font-size: 16px;
  font-weight: 500;
  margin-bottom: 6px;
  color: var(--accent1);
  font-family: var(--mono);
}
.modal p {
  font-size: 13px;
  color: var(--muted);
  line-height: 1.6;
  margin-bottom: 16px;
}
.modal ol {
  font-size: 13px;
  color: var(--text);
  line-height: 1.8;
  padding-left: 20px;
  margin-bottom: 20px;
}
.modal ol li { margin-bottom: 6px; }
.modal ol li a { color: var(--accent1); }
.modal code {
  font-family: var(--mono);
  font-size: 11px;
  background: var(--bg3);
  padding: 2px 6px;
  border-radius: 4px;
  color: var(--accent2);
}
.modal input[type="text"] {
  width: 100%;
  font-family: var(--mono);
  font-size: 12px;
  background: var(--bg3);
  border: 1px solid var(--border2);
  border-radius: 6px;
  padding: 9px 12px;
  color: var(--text);
  outline: none;
  margin-bottom: 12px;
}
.modal input:focus { border-color: var(--accent1); }
.modal-footer {
  display: flex;
  gap: 10px;
  justify-content: flex-end;
  margin-top: 8px;
}

/* ── RESPONSIVE ── */
@media (max-width: 600px) {
  .panel { width: 100vw; }
  .topbar { padding: 12px 16px; }
  .layout { padding: 20px 12px 80px; }
}
</style>
</head>
<body>

<!-- Setup banner -->
<div id="setup-banner">
  <span>⚙ Google Drive sync not configured.</span>
  <a href="#" id="openSetupLink">Click here to set up OAuth</a>
  <span style="color:#a0803a">— notes will save locally until configured.</span>
  <button class="setup-close" id="closeBanner">×</button>
</div>

<!-- Top bar -->
<div class="topbar">
  <div class="logo">SQL_ROADMAP</div>
  <div class="topbar-right">
    <span class="sync-status" id="syncStatus">not signed in</span>
    <button class="btn btn-sm" id="signInBtn">Sign in with Google</button>
    <button class="btn btn-sm" id="signOutBtn" style="display:none">Sign out</button>
  </div>
</div>

<!-- Main layout -->
<div class="layout">
  <div class="progress-row">
    <span class="progress-label" id="progressLabel">0 / 64 topics noted</span>
    <div class="progress-bar-bg">
      <div class="progress-bar-fill" id="progressFill" style="width:0%"></div>
    </div>
  </div>
  <div id="chapters"></div>
</div>

<!-- Notes panel -->
<div class="overlay" id="overlay"></div>
<div class="panel" id="panel">
  <div class="panel-header">
    <button class="panel-close" id="panelClose">×</button>
    <div class="panel-titles">
      <div class="panel-title" id="panelTitle"></div>
      <div class="panel-chapter" id="panelChapter"></div>
    </div>
  </div>
  <div class="panel-body">
    <div class="notes-label">Notes</div>
    <textarea id="notesText" placeholder="Add your notes here...&#10;&#10;Key concepts, examples, things to remember...&#10;&#10;Ctrl+S to save"></textarea>
    <div class="panel-footer">
      <span class="save-hint" id="saveHint">Ctrl+S to save</span>
      <button class="btn btn-sm btn-primary" id="saveBtn">Save</button>
    </div>
  </div>
</div>

<!-- Setup modal -->
<div class="modal-overlay" id="setupModal">
  <div class="modal">
    <h2>// google_oauth_setup</h2>
    <p>To sync notes across devices, you need a free Google OAuth Client ID. Takes about 5 minutes.</p>
    <ol>
      <li>Go to <a href="https://console.cloud.google.com" target="_blank">console.cloud.google.com</a></li>
      <li>Create a new project (e.g. <code>sql-roadmap</code>)</li>
      <li>Go to <strong>APIs & Services → Library</strong>, search for <strong>Google Drive API</strong> and enable it</li>
      <li>Go to <strong>APIs & Services → OAuth consent screen</strong>
        <ul style="margin-top:4px;padding-left:18px;font-size:12px;color:#8b90a0">
          <li>Choose <strong>External</strong>, fill in app name (anything), your email</li>
          <li>Skip scopes for now, add yourself as a test user</li>
        </ul>
      </li>
      <li>Go to <strong>APIs & Services → Credentials → Create Credentials → OAuth Client ID</strong></li>
      <li>Application type: <strong>Web application</strong></li>
      <li>Under <strong>Authorised JavaScript origins</strong>, add your GitHub Pages URL:<br>
        <code>https://dcalabia.github.io</code>
      </li>
      <li>Click Create — copy the <strong>Client ID</strong> below</li>
    </ol>
    <label style="font-size:12px;color:#8b90a0;display:block;margin-bottom:6px">Paste your Client ID:</label>
    <input type="text" id="clientIdInput" placeholder="xxxxxxxxxxxx.apps.googleusercontent.com">
    <div class="modal-footer">
      <button class="btn" id="cancelSetup">Cancel</button>
      <button class="btn btn-primary" id="saveClientId">Save & Sign In</button>
    </div>
  </div>
</div>

<script>
// ── DATA ──────────────────────────────────────────
const CHAPTERS = [
  {n:"01",title:"Introduction",color:"#4a9eff",topics:[
    "What is SQL?","Relational databases","SQL vs NoSQL",
    "Database clients & setup","Your first query"
  ]},
  {n:"02",title:"Query data (SELECT)",color:"#3ecf8e",topics:[
    "SELECT basics","Column aliases","DISTINCT","ORDER BY",
    "LIMIT & OFFSET","Wildcard SELECT *"
  ]},
  {n:"03",title:"Data definition (DDL)",color:"#ff7b54",topics:[
    "CREATE TABLE","Data types","PRIMARY KEY","FOREIGN KEY",
    "ALTER TABLE","DROP TABLE"
  ]},
  {n:"04",title:"Data manipulation (DML)",color:"#a78bfa",topics:[
    "INSERT INTO","UPDATE","DELETE","TRUNCATE",
    "Transactions (BEGIN/COMMIT)","ROLLBACK"
  ]},
  {n:"05",title:"Filtering data",color:"#4a9eff",topics:[
    "WHERE clause","Comparison operators","AND / OR / NOT",
    "IN and NOT IN","BETWEEN","LIKE & wildcards","NULL handling (IS NULL)"
  ]},
  {n:"06",title:"Combining data",color:"#3ecf8e",topics:[
    "INNER JOIN","LEFT / RIGHT JOIN","FULL OUTER JOIN","CROSS JOIN",
    "SELF JOIN","UNION & UNION ALL","Subqueries"
  ]},
  {n:"07",title:"Row-level functions",color:"#ff7b54",topics:[
    "String functions (UPPER, LOWER, TRIM)","Numeric functions (ROUND, ABS)",
    "Date functions (NOW, DATE_PART)","COALESCE & NULLIF",
    "CASE WHEN","Type casting (CAST)"
  ]},
  {n:"08",title:"Aggregation & analytical functions",color:"#a78bfa",topics:[
    "COUNT, SUM, AVG, MIN, MAX","GROUP BY","HAVING",
    "Window functions (ROW_NUMBER)","RANK & DENSE_RANK",
    "LAG & LEAD","PARTITION BY"
  ]},
  {n:"09",title:"Advanced SQL techniques",color:"#4a9eff",topics:[
    "CTEs (WITH clause)","Recursive CTEs","Correlated subqueries",
    "EXISTS & NOT EXISTS","PIVOT / UNPIVOT","JSON in SQL",
    "EXPLAIN & query plans"
  ]},
  {n:"10",title:"Performance optimization",color:"#3ecf8e",topics:[
    "Indexes (B-tree, Hash)","CREATE INDEX","Covering indexes",
    "Execution plans","Query rewriting tips","Partitioning",
    "Vacuuming / statistics"
  ]},
  {n:"11",title:"AI & SQL",color:"#ff7b54",topics:[
    "Prompt engineering for SQL","AI query generation",
    "Text-to-SQL tools","Validating AI output",
    "LLMs + database agents","Use cases & limits"
  ]},
  {n:"12",title:"SQL projects",color:"#a78bfa",topics:[
    "Project: sales analytics","Project: user behavior funnel",
    "Project: trading journal queries","Building a portfolio dataset",
    "Deploying to a live DB","Documentation & presentation"
  ]}
];

const TOTAL_TOPICS = CHAPTERS.reduce((s,c)=>s+c.topics.length,0);

// ── DEFAULT NOTE TEMPLATES ────────────────────────
const DEFAULT_NOTES = {
"ch0_t0": `-- SQL = Structured Query Language
-- Used to interact with relational databases
-- Core operations: SELECT, INSERT, UPDATE, DELETE

-- Simplest possible query
SELECT 'Hello, SQL!' AS message;`,

"ch0_t1": `-- Relational DB = tables (rows + columns) linked by keys
-- users(id, name, email)
-- orders(id, user_id, amount, created_at)
-- user_id in orders references id in users (foreign key)

SELECT * FROM users;
SELECT * FROM orders;`,

"ch0_t2": `-- SQL: structured, schema-enforced, ACID transactions
-- NoSQL: flexible schema, horizontal scaling (MongoDB, Redis)
-- SQL is ideal for: analytics, reporting, joins

-- SQL example
SELECT name, email FROM users WHERE active = true;

-- MongoDB equivalent (not SQL, just reference):
-- db.users.find({ active: true }, { name: 1, email: 1 })`,

"ch0_t3": `-- Popular clients: DBeaver, TablePlus, pgAdmin, DataGrip
-- Cloud: BigQuery, Snowflake, Supabase

-- Test your connection
SELECT version();          -- PostgreSQL
SELECT @@version;          -- MySQL / SQL Server
SELECT sqlite_version();   -- SQLite`,

"ch0_t4": `-- Anatomy of a query
SELECT   column1, column2    -- what to return
FROM     table_name          -- where the data lives
WHERE    condition           -- filter rows
ORDER BY column1 ASC         -- sort results
LIMIT    10;                 -- cap the output

-- Example
SELECT name, email
FROM   users
WHERE  active = true
ORDER BY name ASC
LIMIT 5;`,

"ch1_t0": `-- Select specific columns
SELECT first_name, last_name, email
FROM users;

-- Select all columns
SELECT * FROM users;

-- Select with a calculated column
SELECT name, price, quantity, price * quantity AS total
FROM products;`,

"ch1_t1": `-- AS renames a column in output (doesn't change the table)
SELECT
  first_name        AS "First Name",
  last_name         AS "Last Name",
  email             AS contact,
  price * qty       AS total_value
FROM users;

-- Alias usable in ORDER BY (but NOT in WHERE)
SELECT price * qty AS total_value
FROM orders
ORDER BY total_value DESC;`,

"ch1_t2": `-- Remove duplicate rows from result
SELECT DISTINCT status FROM orders;

-- DISTINCT on multiple columns (combo must be unique)
SELECT DISTINCT city, country FROM customers;

-- Count unique values
SELECT COUNT(DISTINCT user_id) AS unique_buyers
FROM orders;`,

"ch1_t3": `-- Sort ascending (default)
SELECT name, price FROM products ORDER BY price ASC;

-- Sort descending
SELECT name, price FROM products ORDER BY price DESC;

-- Sort by multiple columns
SELECT last_name, first_name FROM users
ORDER BY last_name ASC, first_name ASC;

-- NULLs last (Postgres default for ASC)
SELECT name, score FROM results ORDER BY score ASC NULLS LAST;`,

"ch1_t4": `-- Return first 10 rows
SELECT * FROM orders LIMIT 10;

-- Pagination: page 2 (rows 11-20)
SELECT * FROM orders
ORDER BY created_at DESC
LIMIT 10 OFFSET 10;

-- OFFSET formula: (page_number - 1) * page_size
-- Page 3 = OFFSET 20

-- SQL Server alternative
SELECT TOP 10 * FROM orders;`,

"ch1_t5": `-- Select all columns (use carefully in production)
SELECT * FROM users;

-- Avoid SELECT * in:
-- JOINs (column name collisions)
-- Production queries (fetches unnecessary data)

-- Better: be explicit
SELECT id, name, email, created_at FROM users;

-- BigQuery: exclude one column
SELECT * EXCEPT (password) FROM users;`,

"ch2_t0": `-- Basic CREATE TABLE
CREATE TABLE users (
  id         SERIAL PRIMARY KEY,
  username   VARCHAR(50)  NOT NULL,
  email      VARCHAR(100) UNIQUE NOT NULL,
  created_at TIMESTAMP    DEFAULT NOW()
);

-- Safe version
CREATE TABLE IF NOT EXISTS users (
  id       SERIAL PRIMARY KEY,
  username VARCHAR(50)
);`,

"ch2_t1": `-- Numeric
-- INT, BIGINT, SMALLINT          whole numbers
-- DECIMAL(10,2), NUMERIC(10,2)   exact decimal (money)
-- FLOAT, REAL                    approximate decimal

-- Text
-- VARCHAR(n)   variable length, max n chars
-- CHAR(n)      fixed length
-- TEXT         unlimited length (Postgres)

-- Date/Time
-- DATE          2024-01-15
-- TIMESTAMP     2024-01-15 14:30:00
-- TIMESTAMPTZ   with timezone

-- Other: BOOLEAN, UUID, JSON/JSONB

-- Example
CREATE TABLE trades (
  id          BIGSERIAL    PRIMARY KEY,
  ticker      VARCHAR(10)  NOT NULL,
  entry_price DECIMAL(10,4),
  trade_date  DATE,
  is_winner   BOOLEAN
);`,

"ch2_t2": `-- PRIMARY KEY: uniquely identifies each row, NOT NULL + UNIQUE
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  email VARCHAR(100)
);

-- Composite primary key
CREATE TABLE order_items (
  order_id   INT,
  product_id INT,
  quantity   INT,
  PRIMARY KEY (order_id, product_id)
);

-- UUID primary key
CREATE TABLE sessions (
  id      UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_id INT
);`,

"ch2_t3": `-- FOREIGN KEY links to another table's PRIMARY KEY
CREATE TABLE orders (
  id      SERIAL PRIMARY KEY,
  user_id INT REFERENCES users(id),
  total   DECIMAL(10,2)
);

-- Explicit with ON DELETE behavior
CREATE TABLE orders (
  id      SERIAL PRIMARY KEY,
  user_id INT,
  FOREIGN KEY (user_id)
    REFERENCES users(id)
    ON DELETE CASCADE   -- delete orders when user deleted
    ON UPDATE CASCADE
);
-- ON DELETE options: CASCADE, SET NULL, RESTRICT`,

"ch2_t4": `-- Add a column
ALTER TABLE users ADD COLUMN phone VARCHAR(20);

-- Drop a column
ALTER TABLE users DROP COLUMN phone;

-- Rename a column
ALTER TABLE users RENAME COLUMN username TO user_name;

-- Change data type
ALTER TABLE users ALTER COLUMN phone TYPE TEXT;

-- Add/drop a constraint
ALTER TABLE users ADD CONSTRAINT uq_email UNIQUE (email);
ALTER TABLE users DROP CONSTRAINT uq_email;

-- Rename a table
ALTER TABLE users RENAME TO app_users;`,

"ch2_t5": `-- Drop a table (permanent!)
DROP TABLE users;

-- Safe drop
DROP TABLE IF EXISTS users;

-- Drop multiple tables
DROP TABLE IF EXISTS orders, order_items, products;

-- Drop and cascade to dependents (Postgres)
DROP TABLE users CASCADE;

-- TRUNCATE vs DROP:
TRUNCATE TABLE users;  -- empties table, keeps structure
DROP TABLE users;      -- removes the table entirely`,

"ch3_t0": `-- Insert a single row
INSERT INTO users (name, email)
VALUES ('Dale', 'dale@example.com');

-- Insert multiple rows
INSERT INTO trades (ticker, entry_price, trade_date)
VALUES
  ('AAPL', 189.50, '2024-01-15'),
  ('TSLA', 245.00, '2024-01-16');

-- Insert from another table
INSERT INTO archived_trades
SELECT * FROM trades WHERE trade_date < '2023-01-01';

-- Insert with RETURNING (Postgres)
INSERT INTO users (name, email)
VALUES ('Dale', 'dale@example.com')
RETURNING id, created_at;`,

"ch3_t1": `-- Update matching rows
UPDATE users SET active = false
WHERE last_login < '2023-01-01';

-- Update multiple columns
UPDATE trades
SET
  exit_price = 210.00,
  is_winner  = true,
  pnl        = 210.00 - entry_price
WHERE id = 42;

-- Update with calculation
UPDATE products SET price = price * 1.10;  -- 10% increase

-- Update from another table (Postgres)
UPDATE orders o
SET total = t.sum
FROM (SELECT order_id, SUM(price) AS sum FROM items GROUP BY 1) t
WHERE o.id = t.order_id;

-- Always use WHERE (otherwise updates ALL rows!)`,

"ch3_t2": `-- Delete specific rows
DELETE FROM users WHERE active = false;

-- Delete with multiple conditions
DELETE FROM trades
WHERE pnl < 0 AND trade_date < '2023-01-01';

-- Delete all rows (keeps table structure)
DELETE FROM logs;

-- Delete with RETURNING (Postgres)
DELETE FROM sessions WHERE expires_at < NOW()
RETURNING id, user_id;

-- Always run SELECT first to verify what you're deleting
SELECT * FROM users WHERE active = false;`,

"ch3_t3": `-- Remove all rows quickly (no WHERE clause)
TRUNCATE TABLE logs;

-- TRUNCATE vs DELETE:
-- TRUNCATE: faster, not row-logged, resets sequences
-- DELETE:   slower, logged, allows WHERE, can ROLLBACK

-- Reset auto-increment identity
TRUNCATE TABLE users RESTART IDENTITY;

-- Truncate and cascade to child tables
TRUNCATE TABLE users CASCADE;

-- Truncate multiple tables
TRUNCATE TABLE logs, sessions, temp_data;`,

"ch3_t4": `-- Wrap multiple statements: all succeed or all fail
BEGIN;

  UPDATE accounts SET balance = balance - 500 WHERE id = 1;
  UPDATE accounts SET balance = balance + 500 WHERE id = 2;

COMMIT;

-- SAVEPOINT: partial rollback
BEGIN;
  INSERT INTO orders VALUES (...);
  SAVEPOINT sp1;
  INSERT INTO order_items VALUES (...);  -- fails
  ROLLBACK TO sp1;                       -- undo only items insert
COMMIT;`,

"ch3_t5": `-- ROLLBACK undoes all changes since BEGIN (or last SAVEPOINT)
BEGIN;
  UPDATE accounts SET balance = balance - 1000 WHERE id = 1;
  -- discovered error:
ROLLBACK;  -- balance unchanged

-- Rollback to a savepoint
BEGIN;
  UPDATE users SET plan = 'premium' WHERE id = 5;
  SAVEPOINT after_update;

  DELETE FROM users WHERE id = 5;  -- accidental
  ROLLBACK TO SAVEPOINT after_update;

COMMIT;  -- only the UPDATE is committed`,

"ch4_t0": `-- Filter rows matching a condition
SELECT * FROM users WHERE active = true;

-- Multiple conditions
SELECT * FROM orders
WHERE status = 'shipped' AND total > 100;

-- WHERE with dates
SELECT * FROM trades
WHERE trade_date = '2024-01-15';

-- WHERE with expression
SELECT * FROM products WHERE price * qty > 1000;`,

"ch4_t1": `-- Comparison operators:
-- =    equal
-- <>   not equal (also !=)
-- >    greater than
-- <    less than
-- >=   greater than or equal
-- <=   less than or equal

SELECT * FROM trades WHERE pnl > 0;         -- winners
SELECT * FROM trades WHERE pnl <> 0;        -- not breakeven
SELECT * FROM products WHERE price >= 10 AND price <= 50;`,

"ch4_t2": `-- AND: both conditions must be true
SELECT * FROM trades
WHERE is_winner = true AND pnl > 100;

-- OR: at least one condition must be true
SELECT * FROM users
WHERE plan = 'pro' OR plan = 'enterprise';

-- NOT: negates a condition
SELECT * FROM orders WHERE NOT status = 'cancelled';

-- Parentheses control evaluation order!
SELECT * FROM trades
WHERE (ticker = 'AAPL' OR ticker = 'TSLA')
  AND pnl > 0;`,

"ch4_t3": `-- IN: match any value in a list
SELECT * FROM users
WHERE status IN ('active', 'trial', 'paused');

-- NOT IN: exclude list
SELECT * FROM trades
WHERE ticker NOT IN ('AMTD', 'HMBL');

-- IN with a subquery
SELECT * FROM users
WHERE id IN (SELECT user_id FROM orders WHERE total > 500);

-- Caution: NOT IN with NULLs returns no rows
-- Use NOT EXISTS instead when NULLs are possible`,

"ch4_t4": `-- BETWEEN: inclusive range (same as >= AND <=)
SELECT * FROM trades
WHERE pnl BETWEEN -50 AND 50;  -- includes -50 and 50

-- Date range
SELECT * FROM trades
WHERE trade_date BETWEEN '2024-01-01' AND '2024-12-31';

-- NOT BETWEEN
SELECT * FROM products WHERE price NOT BETWEEN 10 AND 20;

-- For timestamps, prefer explicit >= / < to avoid end-of-day issues:
WHERE trade_date >= '2024-01-01' AND trade_date < '2025-01-01'`,

"ch4_t5": `-- LIKE pattern matching: % = any chars, _ = one char

-- Starts with 'A'
SELECT * FROM tickers WHERE symbol LIKE 'A%';

-- Ends with domain
SELECT * FROM users WHERE email LIKE '%@gmail.com';

-- Contains word
SELECT * FROM courses WHERE title LIKE '%SQL%';

-- Exactly 4 characters
SELECT * FROM codes WHERE code LIKE '____';

-- NOT LIKE
SELECT * FROM products WHERE name NOT LIKE '%Discontinued%';

-- Case-insensitive (Postgres)
SELECT * FROM users WHERE email ILIKE '%gmail%';`,

"ch4_t6": `-- NULL = missing/unknown (NOT the same as 0 or '')
-- Cannot use = or != with NULL

-- Find rows with NULL
SELECT * FROM trades WHERE exit_price IS NULL;

-- Find rows without NULL
SELECT * FROM users WHERE phone IS NOT NULL;

-- COALESCE: return first non-NULL value
SELECT name, COALESCE(phone, 'N/A') AS phone FROM users;

-- NULLIF: return NULL if two values are equal (avoids div by 0)
SELECT 100 / NULLIF(attempts, 0) AS hit_rate FROM stats;

-- NULL in math: any arithmetic with NULL = NULL
SELECT COALESCE(pnl, 0) + 50 AS adjusted FROM trades;`,

"ch5_t0": `-- INNER JOIN: rows matching in BOTH tables only
SELECT
  o.id       AS order_id,
  u.name     AS customer,
  o.total
FROM orders o
INNER JOIN users u ON o.user_id = u.id;

-- JOIN = INNER JOIN (same result)
SELECT t.ticker, j.notes
FROM trades t
JOIN journal j ON t.id = j.trade_id;

-- Join on multiple conditions
SELECT * FROM trades t
JOIN prices p
  ON t.ticker = p.ticker
  AND t.trade_date = p.price_date;`,

"ch5_t1": `-- LEFT JOIN: all rows from LEFT + matching from RIGHT
-- Non-matches from right = NULL
SELECT
  u.name,
  o.id    AS order_id,
  o.total
FROM users u
LEFT JOIN orders o ON u.id = o.user_id;
-- Users with no orders still appear

-- Find users with NO orders (anti-join pattern)
SELECT u.name
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
WHERE o.id IS NULL;

-- RIGHT JOIN = same as LEFT with tables swapped (rarely used)`,

"ch5_t2": `-- FULL OUTER JOIN: all rows from BOTH tables
-- Non-matches on either side = NULL
SELECT
  u.name  AS user_name,
  o.id    AS order_id
FROM users u
FULL OUTER JOIN orders o ON u.id = o.user_id;

-- Find rows in EITHER table with no match
SELECT u.name, o.id
FROM users u
FULL OUTER JOIN orders o ON u.id = o.user_id
WHERE u.id IS NULL OR o.id IS NULL;

-- Not supported in MySQL: simulate with LEFT UNION RIGHT JOIN`,

"ch5_t3": `-- CROSS JOIN: every row in A x every row in B
-- m rows x n rows = m*n rows
SELECT a.color, b.size
FROM colors a
CROSS JOIN sizes b;
-- 3 colors x 4 sizes = 12 combinations

-- Use: generate all date/product combinations
-- Date spine (Postgres)
SELECT generate_series::date AS dt
FROM generate_series('2024-01-01'::date, '2024-12-31', '1 day');

-- Never CROSS JOIN large tables (explodes row count)`,

"ch5_t4": `-- SELF JOIN: a table joined to itself
-- Requires aliases to distinguish the two copies

-- Employee + their manager (same table)
SELECT
  e.name AS employee,
  m.name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.id;

-- Find trades on same ticker, same day
SELECT a.id, b.id, a.ticker
FROM trades a
JOIN trades b
  ON a.ticker = b.ticker
  AND a.trade_date = b.trade_date
  AND a.id < b.id;  -- avoid duplicate pairs`,

"ch5_t5": `-- UNION: combines two queries, removes duplicates
SELECT name FROM customers
UNION
SELECT name FROM suppliers;

-- UNION ALL: keeps duplicates (faster, no dedup)
SELECT ticker FROM trades_2023
UNION ALL
SELECT ticker FROM trades_2024;

-- Rules:
-- Same number of columns in both queries
-- Compatible data types
-- Column names come from the FIRST query

-- Combine historical + current with source label
SELECT id, total, 'historical' AS source FROM old_orders
UNION ALL
SELECT id, total, 'current'    AS source FROM orders;`,

"ch5_t6": `-- Subquery in WHERE
SELECT * FROM trades
WHERE ticker IN (
  SELECT ticker FROM watchlist WHERE priority = 'high'
);

-- Subquery in FROM (derived table / inline view)
SELECT t.ticker, t.avg
FROM (
  SELECT ticker, AVG(pnl) AS avg
  FROM trades GROUP BY ticker
) t
WHERE t.avg > 0;

-- Scalar subquery in SELECT (must return 1 value)
SELECT ticker, pnl,
  (SELECT AVG(pnl) FROM trades) AS overall_avg
FROM trades;

-- Correlated subquery (references outer query)
SELECT * FROM trades t
WHERE pnl > (
  SELECT AVG(pnl) FROM trades WHERE ticker = t.ticker
);`,

"ch6_t0": `-- UPPER / LOWER
SELECT UPPER('hello');              -- 'HELLO'
SELECT LOWER(email) FROM users;

-- TRIM (remove whitespace)
SELECT TRIM('  hello  ');           -- 'hello'
SELECT LTRIM(str), RTRIM(str);

-- LENGTH
SELECT LENGTH('SQL');               -- 3

-- SUBSTRING
SELECT SUBSTRING('Hello World', 1, 5);  -- 'Hello'

-- REPLACE
SELECT REPLACE('foo bar', ' ', '_');    -- 'foo_bar'

-- CONCAT
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM users;
SELECT first_name || ' ' || last_name AS full_name FROM users; -- Postgres

-- POSITION
SELECT POSITION('@' IN email) FROM users;`,

"ch6_t1": `-- ROUND
SELECT ROUND(3.14159, 2);      -- 3.14
SELECT ROUND(pnl, 2) FROM trades;

-- CEIL / FLOOR
SELECT CEIL(4.1);              -- 5
SELECT FLOOR(4.9);             -- 4

-- ABS (absolute value)
SELECT ABS(-25);               -- 25
SELECT ABS(pnl) AS abs_pnl FROM trades;

-- MOD (remainder)
SELECT MOD(10, 3);             -- 1

-- POWER / SQRT
SELECT POWER(2, 10);           -- 1024
SELECT SQRT(144);              -- 12

-- TRUNC (truncate without rounding)
SELECT TRUNC(3.99);            -- 3
SELECT TRUNC(3.99, 1);         -- 3.9`,

"ch6_t2": `-- Current date/time
SELECT NOW();                  -- timestamp with timezone
SELECT CURRENT_DATE;           -- date only

-- Extract parts (Postgres)
SELECT EXTRACT(YEAR  FROM trade_date) AS yr FROM trades;
SELECT EXTRACT(MONTH FROM trade_date) AS mo FROM trades;
SELECT EXTRACT(DOW   FROM trade_date) AS weekday FROM trades;

-- Date arithmetic
SELECT NOW() - INTERVAL '7 days';              -- 7 days ago
SELECT trade_date + INTERVAL '30 days' FROM trades;

-- Date difference
SELECT NOW()::date - trade_date AS days_ago FROM trades;

-- Format date
SELECT TO_CHAR(trade_date, 'YYYY-MM-DD') FROM trades;
SELECT TO_CHAR(NOW(), 'Day, Mon DD YYYY');`,

"ch6_t3": `-- COALESCE: return first non-NULL value
SELECT COALESCE(phone, mobile, 'No contact') AS contact FROM users;

-- Replace NULLs in calculations
SELECT ticker, COALESCE(pnl, 0) AS pnl FROM trades;

-- NULLIF: return NULL if two values are equal
SELECT NULLIF(score, 0);          -- 0 becomes NULL

-- Safe division (avoid divide by zero)
SELECT 100 / NULLIF(attempts, 0) AS hit_rate FROM stats;

-- Practical combo: win rate
SELECT
  wins,
  total,
  ROUND(wins::decimal / NULLIF(total, 0) * 100, 1) AS win_pct
FROM trade_stats;`,

"ch6_t4": `-- CASE: conditional logic inside a query
SELECT
  ticker,
  pnl,
  CASE
    WHEN pnl > 0 THEN 'Winner'
    WHEN pnl < 0 THEN 'Loser'
    ELSE              'Breakeven'
  END AS result
FROM trades;

-- CASE in aggregation (pivot-style counts)
SELECT
  COUNT(CASE WHEN pnl > 0 THEN 1 END) AS winners,
  COUNT(CASE WHEN pnl < 0 THEN 1 END) AS losers
FROM trades;

-- Simple CASE (value matching)
SELECT status,
  CASE status
    WHEN 'A' THEN 'Active'
    WHEN 'I' THEN 'Inactive'
    ELSE 'Unknown'
  END AS label
FROM accounts;`,

"ch6_t5": `-- CAST: convert a value to another data type
SELECT CAST('2024-01-15' AS DATE);
SELECT CAST(price AS INTEGER) FROM products;

-- Postgres shorthand ::
SELECT '2024-01-15'::date;
SELECT price::integer FROM products;
SELECT trade_date::text FROM trades;

-- Safe division (integer / integer = integer in SQL!)
SELECT 7 / 2;              -- 3 (integer division!)
SELECT 7::decimal / 2;     -- 3.5 (cast first)

-- Text to number
SELECT CAST('123.45' AS DECIMAL(10,2));

-- Common gotcha: CAST fails if format doesn't match
-- Use TRY_CAST in SQL Server, or handle in app layer`,

"ch7_t0": `-- COUNT
SELECT COUNT(*)                  AS total_rows     FROM trades;
SELECT COUNT(pnl)                AS non_null_pnl   FROM trades; -- excludes NULLs
SELECT COUNT(DISTINCT ticker)    AS unique_tickers FROM trades;

-- SUM
SELECT SUM(pnl) AS total_pnl FROM trades;
SELECT SUM(CASE WHEN pnl > 0 THEN pnl ELSE 0 END) AS gross_profit FROM trades;

-- AVG
SELECT AVG(pnl) AS avg_pnl FROM trades;

-- MIN / MAX
SELECT MIN(entry_price), MAX(entry_price) FROM trades;
SELECT MIN(trade_date) AS first_trade, MAX(trade_date) AS last_trade FROM trades;`,

"ch7_t1": `-- GROUP BY: aggregate per category
SELECT ticker, COUNT(*) AS trades, SUM(pnl) AS total_pnl
FROM trades
GROUP BY ticker;

-- Multiple columns
SELECT ticker, is_winner, COUNT(*) AS n
FROM trades
GROUP BY ticker, is_winner
ORDER BY ticker;

-- Group by date
SELECT
  trade_date,
  COUNT(*)   AS trades,
  SUM(pnl)   AS daily_pnl
FROM trades
GROUP BY trade_date
ORDER BY trade_date;

-- Every non-aggregated column in SELECT must be in GROUP BY`,

"ch7_t2": `-- HAVING: filter groups (WHERE runs before GROUP, HAVING after)
SELECT ticker, COUNT(*) AS n, SUM(pnl) AS total_pnl
FROM trades
GROUP BY ticker
HAVING COUNT(*) >= 5     -- tickers with 5+ trades
   AND SUM(pnl) > 0;     -- net profitable

-- WHERE vs HAVING together
SELECT ticker, SUM(pnl) AS total_pnl
FROM trades
WHERE trade_date >= '2024-01-01'   -- filter rows first
GROUP BY ticker
HAVING SUM(pnl) > 100;             -- then filter groups`,

"ch7_t3": `-- Window functions: compute across rows WITHOUT collapsing them
-- Unlike GROUP BY, all rows are kept

-- ROW_NUMBER: sequential number per ordering
SELECT trade_date, ticker, pnl,
  ROW_NUMBER() OVER (ORDER BY pnl DESC) AS rank_overall
FROM trades;

-- ROW_NUMBER per partition (restarts per ticker)
SELECT ticker, trade_date, pnl,
  ROW_NUMBER() OVER (PARTITION BY ticker ORDER BY pnl DESC) AS rank_in_ticker
FROM trades;

-- Best trade per ticker
SELECT * FROM (
  SELECT *,
    ROW_NUMBER() OVER (PARTITION BY ticker ORDER BY pnl DESC) AS rn
  FROM trades
) t WHERE rn = 1;`,

"ch7_t4": `-- RANK: ties get same rank, next rank(s) skipped
-- DENSE_RANK: ties get same rank, no gaps

SELECT ticker, pnl,
  RANK()       OVER (ORDER BY pnl DESC) AS rank,
  DENSE_RANK() OVER (ORDER BY pnl DESC) AS dense_rank,
  ROW_NUMBER() OVER (ORDER BY pnl DESC) AS row_num
FROM trades;

-- Example:
-- pnl=500 → rank=1, dense_rank=1
-- pnl=400 → rank=2, dense_rank=2  (tie)
-- pnl=400 → rank=2, dense_rank=2  (tie)
-- pnl=200 → rank=4, dense_rank=3  (rank skips 3!)

-- NTILE: split into N buckets
SELECT ticker, pnl,
  NTILE(4) OVER (ORDER BY pnl) AS quartile
FROM trades;`,

"ch7_t5": `-- LAG: access the previous row's value
-- LEAD: access the next row's value

-- Day-over-day PnL change
SELECT
  trade_date,
  daily_pnl,
  LAG(daily_pnl) OVER (ORDER BY trade_date) AS prev_pnl,
  daily_pnl - LAG(daily_pnl) OVER (ORDER BY trade_date) AS change
FROM daily_summary
ORDER BY trade_date;

-- LAG/LEAD signature: LAG(column, offset, default_if_null)
SELECT trade_date, pnl,
  LEAD(pnl, 1, 0) OVER (ORDER BY trade_date) AS next_pnl
FROM trades;

-- Percent change
SELECT trade_date, pnl,
  ROUND(
    (pnl - LAG(pnl) OVER (ORDER BY trade_date))
    / NULLIF(ABS(LAG(pnl) OVER (ORDER BY trade_date)), 0) * 100
  , 2) AS pct_change
FROM trades;`,

"ch7_t6": `-- PARTITION BY: divide window into groups per category
-- Resets the window calculation per partition

SELECT ticker, trade_date, pnl,
  SUM(pnl)   OVER (PARTITION BY ticker) AS ticker_total,
  COUNT(*)   OVER (PARTITION BY ticker) AS ticker_trades,
  AVG(pnl)   OVER (PARTITION BY ticker) AS ticker_avg,
  SUM(pnl)   OVER (PARTITION BY ticker ORDER BY trade_date) AS running_pnl
FROM trades
ORDER BY ticker, trade_date;

-- PARTITION BY vs GROUP BY:
-- GROUP BY: collapses rows into one per group
-- PARTITION BY: keeps all rows, adds aggregate as a column`,

"ch8_t0": `-- CTE = Common Table Expression: named subquery at the top
-- Improves readability; no performance gain vs subquery

WITH winners AS (
  SELECT ticker, pnl, trade_date
  FROM trades WHERE pnl > 0
),
top_tickers AS (
  SELECT ticker, SUM(pnl) AS total_pnl
  FROM winners GROUP BY ticker
)
SELECT * FROM top_tickers
WHERE total_pnl > 500
ORDER BY total_pnl DESC;

-- CTEs can reference earlier CTEs in the same WITH block
-- Multiple CTEs separated by commas

-- CTE vs subquery:
-- CTE: multi-step logic, reuse result, readability
-- Subquery: single use, simple nesting`,

"ch8_t1": `-- Recursive CTE: references itself, for hierarchical data
-- Structure: anchor UNION ALL recursive member

-- Date series
WITH RECURSIVE date_series AS (
  SELECT '2024-01-01'::date AS dt    -- anchor
  UNION ALL
  SELECT dt + INTERVAL '1 day'       -- recursive step
  FROM date_series
  WHERE dt < '2024-01-31'            -- termination condition
)
SELECT dt FROM date_series;

-- Org chart hierarchy
WITH RECURSIVE org AS (
  SELECT id, name, manager_id, 1 AS level
  FROM employees WHERE manager_id IS NULL
  UNION ALL
  SELECT e.id, e.name, e.manager_id, o.level + 1
  FROM employees e JOIN org o ON e.manager_id = o.id
)
SELECT * FROM org ORDER BY level, name;

-- Always include a termination condition!`,

"ch8_t2": `-- Correlated subquery: inner query references outer query
-- Re-executed for EACH row (can be slow on large sets)

-- Trades where PnL > that ticker's average
SELECT ticker, trade_date, pnl
FROM trades t
WHERE pnl > (
  SELECT AVG(pnl)
  FROM trades
  WHERE ticker = t.ticker   -- references outer row
);

-- Most recent trade per ticker
SELECT * FROM trades t
WHERE trade_date = (
  SELECT MAX(trade_date)
  FROM trades WHERE ticker = t.ticker
);

-- For large data, prefer window functions (much faster):
SELECT * FROM (
  SELECT *,
    RANK() OVER (PARTITION BY ticker ORDER BY trade_date DESC) AS rn
  FROM trades
) t WHERE rn = 1;`,

"ch8_t3": `-- EXISTS: true if subquery returns any row (stops at first match)
SELECT name FROM users u
WHERE EXISTS (
  SELECT 1 FROM orders WHERE user_id = u.id
);

-- NOT EXISTS: users with NO orders
SELECT name FROM users u
WHERE NOT EXISTS (
  SELECT 1 FROM orders WHERE user_id = u.id
);

-- EXISTS vs IN:
-- EXISTS: faster when subquery is large (short-circuits)
-- IN: fine for small value lists
-- NOT EXISTS handles NULLs correctly (NOT IN can fail!)

-- EXISTS with condition
SELECT * FROM tickers t
WHERE EXISTS (
  SELECT 1 FROM trades
  WHERE ticker = t.symbol AND pnl > 0
);`,

"ch8_t4": `-- PIVOT: rotate row values into columns
-- Native syntax: SQL Server / Oracle
SELECT *
FROM (
  SELECT ticker, EXTRACT(MONTH FROM trade_date) AS mo, pnl
  FROM trades
) src
PIVOT (
  SUM(pnl)
  FOR mo IN ([1],[2],[3],[4],[5],[6])
) pvt;

-- Postgres PIVOT with CASE WHEN (manual)
SELECT ticker,
  SUM(CASE WHEN mo = 1 THEN pnl END) AS jan,
  SUM(CASE WHEN mo = 2 THEN pnl END) AS feb,
  SUM(CASE WHEN mo = 3 THEN pnl END) AS mar
FROM (
  SELECT ticker, EXTRACT(MONTH FROM trade_date)::int AS mo, pnl
  FROM trades
) t
GROUP BY ticker;

-- UNPIVOT: rotate columns back to rows (reverse of pivot)`,

"ch8_t5": `-- Postgres JSONB (binary JSON, faster for querying)
CREATE TABLE events (
  id   SERIAL PRIMARY KEY,
  data JSONB
);

INSERT INTO events (data)
VALUES ('{"user_id":1,"action":"buy","ticker":"AAPL","qty":10}');

-- Access a key: ->  returns JSON, ->> returns text
SELECT data->>'ticker' AS ticker FROM events;
SELECT data->'qty'     AS qty    FROM events;

-- Filter on JSON field
SELECT * FROM events WHERE data->>'action' = 'buy';

-- Nested JSON
SELECT data->'address'->>'city' AS city FROM users;

-- Expand JSON array
SELECT jsonb_array_elements(data->'tags') AS tag FROM articles;

-- Update JSON field
UPDATE events
SET data = data || '{"filled": true}'
WHERE id = 1;`,

"ch8_t6": `-- EXPLAIN: shows how DB plans to run your query (no execution)
EXPLAIN SELECT * FROM trades WHERE ticker = 'AAPL';

-- EXPLAIN ANALYZE: actually runs it, shows real timings
EXPLAIN ANALYZE SELECT * FROM trades WHERE ticker = 'AAPL';

-- Key things to look for:
-- Seq Scan     = reads entire table (no index used)
-- Index Scan   = uses an index (fast)
-- Hash Join    = joining via hashing
-- Nested Loop  = row-by-row join (slow on large sets)

-- cost=X..Y: startup..total cost (arbitrary units)
-- rows=N: estimated row count
-- actual time=X..Y ms: real timing (ANALYZE only)

-- With buffer stats (Postgres)
EXPLAIN (ANALYZE, BUFFERS)
SELECT * FROM trades WHERE pnl > 0;`,

"ch9_t0": `-- Index: speeds up lookups (like a book index)
-- Trade-off: faster reads, slower writes, uses disk space

-- B-tree (default): good for =, <, >, BETWEEN, LIKE 'x%'
CREATE INDEX idx_trades_ticker ON trades(ticker);

-- Hash: equality only (= only), faster than B-tree for =
CREATE INDEX idx_users_email_hash ON users USING HASH (email);

-- When indexes help:
-- Columns in WHERE, JOIN ON, ORDER BY, GROUP BY
-- High-cardinality columns (many unique values)

-- When they don't help:
-- Very small tables
-- Low-cardinality (e.g., is_active = true/false)
-- Rarely queried columns

-- Verify index is used:
EXPLAIN SELECT * FROM trades WHERE ticker = 'AAPL';`,

"ch9_t1": `-- Basic index
CREATE INDEX idx_trades_ticker ON trades(ticker);

-- Unique index (enforces uniqueness + speeds up lookups)
CREATE UNIQUE INDEX idx_users_email ON users(email);

-- Composite index (column order matters!)
CREATE INDEX idx_trades_ticker_date ON trades(ticker, trade_date);
-- Good for: WHERE ticker = 'X'
-- Good for: WHERE ticker = 'X' AND trade_date = 'Y'
-- Bad for:  WHERE trade_date = 'Y' only

-- Partial index (only indexes matching rows)
CREATE INDEX idx_active_users ON users(email) WHERE active = true;

-- Expression index
CREATE INDEX idx_lower_email ON users(LOWER(email));

-- Drop / list indexes
DROP INDEX IF EXISTS idx_trades_ticker;
SELECT indexname, indexdef FROM pg_indexes WHERE tablename = 'trades';`,

"ch9_t2": `-- Covering index: includes ALL columns the query needs
-- Query answered entirely from index (no table lookup = faster)

-- Query: SELECT ticker, pnl FROM trades WHERE ticker = 'AAPL'
-- Covering index (INCLUDE adds extra columns to index)
CREATE INDEX idx_trades_covering
ON trades(ticker) INCLUDE (pnl);

-- Without covering index: Index Scan + heap fetch per row
-- With covering index: Index Only Scan (much faster)

-- Verify with EXPLAIN (look for "Index Only Scan"):
EXPLAIN SELECT ticker, pnl FROM trades WHERE ticker = 'AAPL';

-- Full composite covering index
CREATE INDEX idx_trades_full
ON trades(ticker, trade_date) INCLUDE (pnl, entry_price);
-- Covers: WHERE ticker + ORDER BY trade_date + SELECT pnl, entry_price`,

"ch9_t3": `-- How to read EXPLAIN ANALYZE output

EXPLAIN ANALYZE
SELECT ticker, SUM(pnl)
FROM trades
WHERE trade_date >= '2024-01-01'
GROUP BY ticker;

-- Read plan bottom-up:
-- Seq Scan on trades
--   Filter: trade_date >= '2024-01-01'
--   Rows Removed by Filter: 1500
-- HashAggregate (GROUP BY ticker)

-- Key metrics:
-- actual time=X..Y  startup..total ms
-- rows=N            rows output by this node
-- loops=N           how many times node ran

-- Warning signs:
-- Seq Scan on large table (missing index)
-- Estimated rows >> actual rows (stale stats: run ANALYZE)
-- Nested Loop on large sets (memory pressure)

-- Test if index would help:
SET enable_seqscan = OFF;
EXPLAIN SELECT * FROM trades WHERE ticker = 'AAPL';`,

"ch9_t4": `-- 1. Use EXISTS instead of IN for large subqueries
-- Slow:
SELECT * FROM users WHERE id IN (SELECT user_id FROM orders);
-- Fast:
SELECT * FROM users u
WHERE EXISTS (SELECT 1 FROM orders WHERE user_id = u.id);

-- 2. Avoid functions on indexed columns in WHERE
-- Slow (index skipped):
WHERE EXTRACT(YEAR FROM trade_date) = 2024
-- Fast:
WHERE trade_date >= '2024-01-01' AND trade_date < '2025-01-01'

-- 3. Use UNION ALL instead of UNION (skip dedup if not needed)
-- 4. Push filters early -- filter before joining
-- 5. Avoid SELECT * -- only fetch needed columns
-- 6. Use CTEs or temp tables for repeated subqueries
-- 7. LIMIT early when you only need a few rows`,

"ch9_t5": `-- Partitioning: split large table into physical chunks
-- Improves performance via partition pruning

-- Range partitioning by date (Postgres)
CREATE TABLE trades (
  id         BIGSERIAL,
  ticker     VARCHAR(10),
  trade_date DATE,
  pnl        DECIMAL(10,2)
) PARTITION BY RANGE (trade_date);

-- Create year partitions
CREATE TABLE trades_2023 PARTITION OF trades
  FOR VALUES FROM ('2023-01-01') TO ('2024-01-01');

CREATE TABLE trades_2024 PARTITION OF trades
  FOR VALUES FROM ('2024-01-01') TO ('2025-01-01');

-- Query auto-prunes to relevant partition:
SELECT * FROM trades WHERE trade_date >= '2024-01-01';
-- Only scans trades_2024

-- List partitioning
CREATE TABLE trades PARTITION BY LIST (market);
CREATE TABLE trades_us PARTITION OF trades FOR VALUES IN ('NYSE','NASDAQ');`,

"ch9_t6": `-- Postgres uses MVCC: dead rows accumulate after UPDATE/DELETE
-- VACUUM reclaims that space

-- Manual vacuum (reclaim dead row space)
VACUUM trades;

-- VACUUM FULL (compact table -- locks table, use rarely)
VACUUM FULL trades;

-- VACUUM ANALYZE (reclaim + update planner stats)
VACUUM ANALYZE trades;

-- ANALYZE: update planner statistics only
ANALYZE trades;

-- Check table bloat and last vacuum
SELECT
  relname       AS table_name,
  n_dead_tup    AS dead_rows,
  last_vacuum,
  last_autovacuum
FROM pg_stat_user_tables
WHERE relname = 'trades';

-- autovacuum handles this automatically in most setups`,

"ch10_t0": `-- Tips for getting good SQL from AI

-- 1. Provide schema context
-- "Table: trades (id, ticker, entry_price, exit_price, pnl, trade_date, is_winner)"

-- 2. Specify the database
-- "Write this in PostgreSQL syntax"

-- 3. Describe input + expected output
-- "Given daily_pnl per trade_date, return a 7-day rolling average"

-- 4. State constraints
-- "Avoid subqueries, use a CTE instead"
-- "Must use an index on ticker"

-- 5. Ask for explanation
-- "Explain each step of the query"

-- Example prompt:
-- "PostgreSQL. Table: trades(id, ticker, pnl, trade_date).
--  Write a query showing each ticker's win rate and total PnL
--  for tickers with 5+ trades. Use a CTE. Explain each section."`,

"ch10_t1": `-- AI tools that generate SQL:
-- ChatGPT / Claude: best for complex logic + explanation
-- GitHub Copilot: inline suggestions in IDE
-- Cursor: AI-native IDE, great for .sql files
-- DBeaver AI: built into the DB client

-- Workflow:
-- 1. Paste your schema (CREATE TABLE statements)
-- 2. Describe the business question in plain English
-- 3. Review and validate the generated SQL
-- 4. Run EXPLAIN ANALYZE to check performance
-- 5. Test edge cases: NULLs, empty tables, duplicates

-- Prompt template:
-- "Schema: [paste CREATE TABLE statements]
--  Question: [plain English description]
--  Requirements:
--  - Database: PostgreSQL
--  - Use CTE structure
--  - Must use index on [column]"`,

"ch10_t2": `-- Dedicated text-to-SQL tools:

-- vanna.ai
--   Open source, trains on your schema, self-hostable

-- defog.ai / sqlcoder
--   Open-source LLM fine-tuned for SQL

-- Outerbase / cardinal.so
--   Chat interface over your database

-- Retool / Metabase AI
--   Built-in natural language queries, dashboard-focused

-- Claude / GPT-4 with schema context
--   Most flexible, best for complex one-off queries

-- Accuracy factors:
-- Clear column naming
-- Table documentation / comments
-- Sample data in prompt
-- Database dialect specified`,

"ch10_t3": `-- Never run AI SQL on production without checking:

-- 1. Read line by line -- understand every clause
-- 2. Verify table/column names match your schema
-- 3. Check for missing WHERE on UPDATE/DELETE!
-- 4. Run on dev/staging DB first
-- 5. EXPLAIN ANALYZE -- check cost and row estimates
-- 6. Test edge cases:
--    - Empty table
--    - NULLs in key columns
--    - Duplicate rows
--    - Boundary dates

-- Sanity checks:
SELECT COUNT(*) FROM trades;
SELECT COUNT(*) FROM trades WHERE [condition];

-- Wrap risky changes in a transaction
BEGIN;
  [AI-generated UPDATE or DELETE];
  SELECT COUNT(*) FROM trades WHERE [condition]; -- verify
ROLLBACK;  -- change to COMMIT only when confirmed`,

"ch10_t4": `-- Database agents: LLMs that autonomously query a DB

-- How they work:
-- 1. LLM receives schema + user question
-- 2. LLM generates SQL
-- 3. Agent executes query against DB
-- 4. LLM interprets results and responds

-- Tools:
-- LangChain SQLDatabaseChain
-- LlamaIndex SQL query engine
-- OpenAI function calling + DB tool
-- Claude with tool use + DB connector

-- Safety rules for agents:
-- Use a read-only DB user
-- Validate all generated SQL before execution
-- Rate limit queries
-- Log every agent-generated query
-- Never give agents write access to production`,

"ch10_t5": `-- Where AI + SQL works well:
-- Exploratory queries on known schemas
-- Translating business questions to SQL
-- Writing boilerplate (CRUD, aggregations)
-- Explaining query logic
-- Suggesting optimizations

-- Where it struggles:
-- Complex multi-step business logic
-- Ambiguous column names or schemas
-- DB-specific syntax and dialects
-- Performance-critical queries without context
-- Security-sensitive operations

-- Accuracy (Spider/BIRD benchmarks):
-- GPT-4: ~85%   Claude: ~83-86%
-- Drops significantly on complex multi-table queries

-- Best practice: AI as first draft
-- Human reviews and owns the final query
-- Document AI-generated queries in your codebase`,

"ch11_t0": `-- Schema:
-- orders(id, customer_id, created_at, total, status)
-- order_items(id, order_id, product_id, qty, unit_price)
-- products(id, name, category, cost_price)
-- customers(id, name, region, signup_date)

-- Monthly revenue
SELECT DATE_TRUNC('month', created_at) AS month,
       SUM(total) AS revenue
FROM orders WHERE status = 'completed'
GROUP BY 1 ORDER BY 1;

-- Top 10 products by revenue
SELECT p.name, SUM(oi.qty * oi.unit_price) AS revenue
FROM order_items oi JOIN products p ON oi.product_id = p.id
GROUP BY p.name ORDER BY revenue DESC LIMIT 10;

-- Month-over-month growth
SELECT month, revenue,
  LAG(revenue) OVER (ORDER BY month) AS prev,
  ROUND((revenue / NULLIF(LAG(revenue) OVER (ORDER BY month), 0) - 1) * 100, 1) AS pct_change
FROM (...) monthly;`,

"ch11_t1": `-- Schema:
-- events(id, user_id, event_type, created_at, metadata JSONB)
-- event_types: 'signup','onboarding','first_trade','subscription'

-- Conversion funnel
WITH funnel AS (
  SELECT
    COUNT(DISTINCT CASE WHEN event_type = 'signup'       THEN user_id END) AS signups,
    COUNT(DISTINCT CASE WHEN event_type = 'onboarding'   THEN user_id END) AS onboarded,
    COUNT(DISTINCT CASE WHEN event_type = 'first_trade'  THEN user_id END) AS activated,
    COUNT(DISTINCT CASE WHEN event_type = 'subscription' THEN user_id END) AS converted
  FROM events
)
SELECT *,
  ROUND(onboarded::decimal / NULLIF(signups,   0) * 100, 1) AS onboard_rate,
  ROUND(activated::decimal / NULLIF(onboarded, 0) * 100, 1) AS activation_rate,
  ROUND(converted::decimal / NULLIF(activated, 0) * 100, 1) AS conversion_rate
FROM funnel;

-- Time to first trade (avg days)
SELECT AVG(EXTRACT(EPOCH FROM (ft.created_at - s.created_at)) / 86400) AS avg_days
FROM events s
JOIN events ft ON s.user_id = ft.user_id
WHERE s.event_type = 'signup' AND ft.event_type = 'first_trade';`,

"ch11_t2": `-- Schema: trades(id, ticker, trade_date, entry_price, exit_price,
--              shares, pnl, is_winner, setup, notes, session)

-- Overall stats
SELECT
  COUNT(*)                                         AS total_trades,
  ROUND(AVG(CASE WHEN is_winner THEN 1.0 ELSE 0 END) * 100, 1) AS win_rate_pct,
  SUM(pnl)                                         AS total_pnl,
  AVG(pnl)                                         AS avg_pnl,
  SUM(CASE WHEN is_winner THEN pnl ELSE 0 END)
    / NULLIF(ABS(SUM(CASE WHEN NOT is_winner THEN pnl ELSE 0 END)), 0) AS profit_factor
FROM trades;

-- Best/worst setups
SELECT setup, COUNT(*) AS n,
  ROUND(AVG(CASE WHEN is_winner THEN 1.0 ELSE 0 END) * 100, 1) AS win_rate,
  SUM(pnl) AS total_pnl
FROM trades GROUP BY setup ORDER BY total_pnl DESC;

-- Daily PnL with running total
SELECT trade_date, SUM(pnl) AS daily_pnl,
  SUM(SUM(pnl)) OVER (ORDER BY trade_date) AS running_pnl
FROM trades GROUP BY trade_date ORDER BY trade_date;`,

"ch11_t3": `-- Load CSV to Postgres
COPY trades (ticker, trade_date, entry_price, exit_price, pnl)
FROM '/path/to/trades.csv'
WITH (FORMAT csv, HEADER true);

-- Client-side copy in psql
\copy trades FROM 'trades.csv' CSV HEADER;

-- Create a practice schema
CREATE SCHEMA portfolio;
CREATE TABLE portfolio.trades (...);
CREATE TABLE portfolio.tickers (
  symbol       VARCHAR(10),
  sector       VARCHAR(50),
  float_shares BIGINT
);

-- Document your schema
COMMENT ON TABLE trades IS 'Personal trading journal -- small cap momentum';
COMMENT ON COLUMN trades.pnl IS 'Net PnL in USD after commissions';

-- Public datasets: Kaggle, SQLZoo, Northwind DB
-- Export Questrade trades as CSV then load above`,

"ch11_t4": `-- Free hosting options:
-- Supabase: generous free tier, REST API + auth built in
-- Neon.tech: serverless Postgres, Git-like branching
-- Railway: 500hr/month free
-- ElephantSQL: 20MB free tier

-- Connect from Python (psycopg2)
import psycopg2
conn = psycopg2.connect(
  host="your-host.db.com",
  database="trading",
  user="dale",
  password="..."
)

-- Connect via SQLAlchemy
from sqlalchemy import create_engine
engine = create_engine("postgresql://dale:pass@host/trading")

-- Connect from Power BI:
-- Data Source > PostgreSQL > host, DB, credentials

-- Always use environment variables for secrets!
import os
conn_str = os.environ.get("DATABASE_URL")`,

"ch11_t5": `/*
  Query: Daily PnL Summary
  Description: Aggregates trades by date, computes
               daily P&L and cumulative running total
*/

SELECT
  trade_date,
  SUM(pnl) AS daily_pnl,
  SUM(SUM(pnl)) OVER (ORDER BY trade_date) AS running_pnl
FROM trades
GROUP BY trade_date
ORDER BY trade_date;

-- Portfolio presentation checklist:
-- 1. State the business question above each query
-- 2. Show expected output (screenshot or table)
-- 3. Explain approach choices (CTE vs subquery, etc.)
-- 4. EXPLAIN ANALYZE screenshot for perf queries
-- 5. GitHub repo: one .sql file per project chapter
-- 6. README.md with schema diagram + query index

-- Visualization tools:
-- Power BI / Tableau: connect directly to Postgres
-- Metabase: open source, self-host
-- Redash: good for SQL-first teams`
};

// ── STATE ─────────────────────────────────────────
let notes = {};      // { "ch0_t2": "my note text", ... }
let currentKey = null;
let driveFileId = null;
let isSyncing = false;
let CLIENT_ID = localStorage.getItem('sql_client_id') || '';
const SCOPE = 'https://www.googleapis.com/auth/drive.appdata';
const FILE_NAME = 'sql_notes.json';

// ── BUILD UI ──────────────────────────────────────
function buildChapters() {
  const container = document.getElementById('chapters');
  container.innerHTML = '';
  CHAPTERS.forEach((ch, ci) => {
    const div = document.createElement('div');
    div.className = 'chapter';
    div.innerHTML = `
      <div class="chapter-header" data-ci="${ci}">
        <span class="ch-num">#${ch.n}</span>
        <span class="ch-dot" style="background:${ch.color}"></span>
        <span class="ch-title">${ch.title}</span>
        <span class="ch-count">${ch.topics.length} topics</span>
        <span class="ch-arrow">›</span>
      </div>
      <div class="subtopics">
        ${ch.topics.map((t,ti) => {
          const key = `ch${ci}_t${ti}`;
          return `<div class="subtopic" data-key="${key}"
            data-topic="${t.replace(/"/g,'&quot;')}"
            data-chapter="${ch.title.replace(/"/g,'&quot;')}">
            <span class="note-dot"></span>
            <span class="subtopic-label">${t}</span>
            <span class="subtopic-meta">notes ›</span>
          </div>`;
        }).join('')}
      </div>`;
    container.appendChild(div);
  });

  container.addEventListener('click', e => {
    const hdr = e.target.closest('.chapter-header');
    if (hdr) {
      hdr.closest('.chapter').classList.toggle('open');
      return;
    }
    const st = e.target.closest('.subtopic');
    if (st) openPanel(
      st.dataset.key,
      st.dataset.topic,
      st.dataset.chapter
    );
  });
}

function refreshDots() {
  document.querySelectorAll('.subtopic').forEach(el => {
    const key = el.dataset.key;
    const has = !!(notes[key] && notes[key].trim());
    el.classList.toggle('has-note', has);
  });
  const noted = Object.values(notes).filter(v=>v&&v.trim()).length;
  document.getElementById('progressLabel').textContent =
    `${noted} / ${TOTAL_TOPICS} topics noted`;
  document.getElementById('progressFill').style.width =
    `${Math.round(noted/TOTAL_TOPICS*100)}%`;
}

// ── NOTES PANEL ───────────────────────────────────
const panel = document.getElementById('panel');
const overlay = document.getElementById('overlay');

function openPanel(key, topic, chapter) {
  currentKey = key;
  document.getElementById('panelTitle').textContent = topic;
  document.getElementById('panelChapter').textContent =
    'Chapter: ' + chapter;
  document.getElementById('notesText').value = notes[key] || '';
  document.getElementById('saveHint').textContent = 'Ctrl+S to save';
  document.getElementById('saveHint').className = 'save-hint';
  panel.classList.add('open');
  overlay.classList.add('open');
  setTimeout(() => document.getElementById('notesText').focus(), 260);
}

function closePanel() {
  panel.classList.remove('open');
  overlay.classList.remove('open');
  currentKey = null;
}

function saveNote() {
  if (!currentKey) return;
  const val = document.getElementById('notesText').value;
  if (val.trim()) {
    notes[currentKey] = val;
  } else {
    delete notes[currentKey];
  }
  refreshDots();
  persistLocal();
  const hint = document.getElementById('saveHint');
  hint.textContent = '✓ saved';
  hint.className = 'save-hint save-ok';
  setTimeout(() => {
    hint.textContent = 'Ctrl+S to save';
    hint.className = 'save-hint';
  }, 1800);
  if (isSignedIn()) syncToDrive();
}

document.getElementById('panelClose').addEventListener('click', closePanel);
overlay.addEventListener('click', closePanel);
document.getElementById('saveBtn').addEventListener('click', saveNote);
document.getElementById('notesText').addEventListener('keydown', e => {
  if ((e.ctrlKey || e.metaKey) && e.key === 's') {
    e.preventDefault();
    saveNote();
  }
});

// ── LOCAL FALLBACK ────────────────────────────────
function persistLocal() {
  localStorage.setItem('sql_notes_local', JSON.stringify(notes));
}

function loadLocal() {
  const raw = localStorage.getItem('sql_notes_local');
  if (raw) { try { notes = JSON.parse(raw); } catch(e) {} }
}

// ── GOOGLE DRIVE SYNC ─────────────────────────────
let tokenClient;
let accessToken = null;

function loadGsi() {
  return new Promise(resolve => {
    if (window.google && window.google.accounts) { resolve(); return; }
    const s = document.createElement('script');
    s.src = 'https://accounts.google.com/gsi/client';
    s.onload = resolve;
    document.head.appendChild(s);
  });
}

function isSignedIn() { return !!accessToken; }

function setSyncStatus(msg, cls) {
  const el = document.getElementById('syncStatus');
  el.textContent = msg;
  el.className = 'sync-status' + (cls ? ' ' + cls : '');
}

async function initAuth() {
  if (!CLIENT_ID) return;
  await loadGsi();
  tokenClient = google.accounts.oauth2.initTokenClient({
    client_id: CLIENT_ID,
    scope: SCOPE,
    callback: async (resp) => {
      if (resp.error) {
        setSyncStatus('auth error', 'err');
        return;
      }
      accessToken = resp.access_token;
      document.getElementById('signInBtn').style.display = 'none';
      document.getElementById('signOutBtn').style.display = '';
      setSyncStatus('syncing…');
      await loadFromDrive();
      refreshDots();
      setSyncStatus('synced ✓', 'ok');
    }
  });
}

document.getElementById('signInBtn').addEventListener('click', async () => {
  if (!CLIENT_ID) {
    document.getElementById('setupModal').classList.add('open');
    return;
  }
  if (!tokenClient) await initAuth();
  tokenClient.requestAccessToken({ prompt: 'consent' });
});

document.getElementById('signOutBtn').addEventListener('click', () => {
  if (accessToken) {
    google.accounts.oauth2.revoke(accessToken);
    accessToken = null;
  }
  document.getElementById('signInBtn').style.display = '';
  document.getElementById('signOutBtn').style.display = 'none';
  setSyncStatus('signed out');
});

async function driveRequest(method, url, body) {
  const headers = { 'Authorization': 'Bearer ' + accessToken };
  if (body && typeof body === 'object' && !(body instanceof Blob)) {
    // multipart handled separately
  }
  const opts = { method, headers };
  if (body) opts.body = body;
  const res = await fetch(url, opts);
  if (!res.ok) throw new Error(await res.text());
  return res;
}

async function findDriveFile() {
  const res = await driveRequest(
    'GET',
    `https://www.googleapis.com/drive/v3/files?spaces=appDataFolder` +
    `&q=name%3D%27${FILE_NAME}%27&fields=files(id)`
  );
  const data = await res.json();
  return data.files && data.files[0] ? data.files[0].id : null;
}

async function loadFromDrive() {
  try {
    const id = await findDriveFile();
    if (!id) { driveFileId = null; return; }
    driveFileId = id;
    const res = await driveRequest(
      'GET',
      `https://www.googleapis.com/drive/v3/files/${id}?alt=media`
    );
    const remote = await res.json();
    // merge: remote wins over local
    notes = Object.assign({}, notes, remote);
    persistLocal();
  } catch(e) {
    console.warn('Drive load error:', e);
  }
}

async function syncToDrive() {
  if (!accessToken || isSyncing) return;
  isSyncing = true;
  setSyncStatus('syncing…');
  try {
    const blob = new Blob(
      [JSON.stringify(notes)],
      { type: 'application/json' }
    );
    if (driveFileId) {
      // update existing
      const form = new FormData();
      form.append('file', blob, FILE_NAME);
      await fetch(
        `https://www.googleapis.com/upload/drive/v3/files/${driveFileId}` +
        `?uploadType=multipart`,
        {
          method: 'PATCH',
          headers: { 'Authorization': 'Bearer ' + accessToken },
          body: form
        }
      );
    } else {
      // create new in appDataFolder
      const meta = JSON.stringify({
        name: FILE_NAME,
        parents: ['appDataFolder']
      });
      const form = new FormData();
      form.append('metadata',
        new Blob([meta], { type: 'application/json' })
      );
      form.append('file', blob, FILE_NAME);
      const res = await fetch(
        'https://www.googleapis.com/upload/drive/v3/files' +
        '?uploadType=multipart&fields=id',
        {
          method: 'POST',
          headers: { 'Authorization': 'Bearer ' + accessToken },
          body: form
        }
      );
      const data = await res.json();
      driveFileId = data.id;
    }
    setSyncStatus('synced ✓', 'ok');
  } catch(e) {
    setSyncStatus('sync error', 'err');
    console.warn('Drive sync error:', e);
  }
  isSyncing = false;
}

// ── SETUP MODAL ───────────────────────────────────
document.getElementById('openSetupLink')
  .addEventListener('click', e => {
    e.preventDefault();
    document.getElementById('setupModal').classList.add('open');
  });
document.getElementById('cancelSetup')
  .addEventListener('click', () => {
    document.getElementById('setupModal').classList.remove('open');
  });
document.getElementById('saveClientId')
  .addEventListener('click', async () => {
    const val = document.getElementById('clientIdInput')
      .value.trim();
    if (!val) return;
    CLIENT_ID = val;
    localStorage.setItem('sql_client_id', CLIENT_ID);
    document.getElementById('setupModal').classList.remove('open');
    document.getElementById('setup-banner').classList.add('hidden');
    await initAuth();
    tokenClient.requestAccessToken({ prompt: 'consent' });
  });
document.getElementById('closeBanner')
  .addEventListener('click', () => {
    document.getElementById('setup-banner').classList.add('hidden');
  });

// ── INIT ──────────────────────────────────────────
async function init() {
  loadLocal();
  // Apply default templates for any topic not yet written by the user
  Object.keys(DEFAULT_NOTES).forEach(key => {
    if (!notes[key] || !notes[key].trim()) {
      notes[key] = DEFAULT_NOTES[key];
    }
  });
  buildChapters();
  refreshDots();

  if (CLIENT_ID) {
    document.getElementById('setup-banner')
      .classList.add('hidden');
    await initAuth();
  }
}

init();
</script>
</body>
</html>
