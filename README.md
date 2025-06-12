# graphql-express-mongodb-starter
# GraphQL API Starter with Express & MongoDB

هذا المشروع هو نقطة بداية (Starter) لبناء واجهة برمجة تطبيقات (API) باستخدام GraphQL، مع خادم Express.js، وقاعدة بيانات MongoDB. تم استخدام مكتبة `graphql-yoga` لتسهيل إعداد خادم GraphQL.

This is a starter project for building a GraphQL API using Node.js, Express, GraphQL Yoga, and MongoDB.

---

## الميزات (Features)

-   **خادم GraphQL متكامل**: إعداد سريع لخادم GraphQL باستخدام Express و GraphQL Yoga.
-   **عمليات CRUD للمستخدمين**: إنشاء، قراءة، تحديث، وحذف المستخدمين (Users).
-   **عمليات قراءة للتعليقات**: جلب التعليقات (Comments).
-   **علاقات بين البيانات (Resolvers)**:
    -   جلب كل تعليقات مستخدم معين.
    -   جلب بيانات المستخدم صاحب تعليق معين.
-   **اتصال بقاعدة البيانات**: إعداد للاتصال بـ MongoDB Atlas.
-   **واجهة اختبار مدمجة**: استخدام Ruru كواجهة رسومية (IDE) لاختبار استعلامات GraphQL مباشرة من المتصفح.

---

## التقنيات المستخدمة (Tech Stack)

-   [Node.js](https://nodejs.org/) - بيئة تشغيل JavaScript.
-   [Express.js](https://expressjs.com/) - إطار عمل لبناء الخادم.
-   [GraphQL Yoga](https://the-guild.dev/graphql/yoga-server) - خادم GraphQL متكامل.
-   [MongoDB](https://www.mongodb.com/) - قاعدة بيانات NoSQL.
-   [Ruru](https://the-guild.dev/graphql/ruru) - واجهة رسومية لاختبار GraphQL.

---

## المتطلبات الأساسية (Prerequisites)

-   تثبيت [Node.js](https://nodejs.org/en/download/) (إصدار 16 أو أحدث).
-   حساب على [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) للحصول على رابط اتصال بقاعدة البيانات.

---

## التثبيت والتشغيل (Installation & Setup)

1.  **نسخ المستودع (Clone the repository):**
    ```bash
    git clone  https://github.com/Abdulrahman-haytham/graphql-express-mongodb-starter.git
    cd graphql-express-mongodb-starter
    ```

2.  **تثبيت الحزم (Install dependencies):**
    ```bash
    npm install
    ```

3.  **إعداد متغيرات البيئة (Set up environment variables):**
    -   أنشئ ملفاً جديداً في المجلد الرئيسي باسم `.env`.
    -   أضف رابط الاتصال بقاعدة بيانات MongoDB الخاصة بك داخل الملف:
    ```
    MONGO_URI="your_mongodb_connection_string"
    ```

4.  **تشغيل الخادم (Start the server):**
    ```bash
    npm start
    ```

الخادم سيعمل الآن على `http://localhost:4000`.

---

## طريقة الاستخدام (Usage)

-   **واجهة الاختبار (GraphQL IDE):** افتح المتصفح على `http://localhost:4000` للوصول إلى واجهة Ruru وكتابة الاستعلامات.
-   **نقطة النهاية (API Endpoint):** نقطة النهاية للـ API هي `http://localhost:4000/graphql`.

### أمثلة على الاستعلامات (Example Queries)

#### جلب جميع المستخدمين
```graphql
query GetAllUsers {
  users {
    id
    name
    email
    comments {
      text
    }
  }
}

جلب مستخدم واحد بالـ ID مع تعليقاته
query GetSingleUser {
  user(id: "YOUR_USER_ID") {
    id
    name
    email
    comments {
      _id
      text
    }
  }
}
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Graphql
IGNORE_WHEN_COPYING_END
إنشاء مستخدم جديد (Mutation)
mutation CreateNewUser {
  createUser(user: { name: "Ali Hassan", email: "ali@example.com" }) {
    id
    name
    email
  }
}
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Graphql
IGNORE_WHEN_COPYING_END
تحديث اسم مستخدم
mutation UpdateUserName {
  updateUser(id: "YOUR_USER_ID", update: { name: "New Updated Name" }) {
    id
    name
  }
}
