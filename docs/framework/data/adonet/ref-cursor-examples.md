---
title: REF CURSOR Örnekleri
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: dfad86c6d5c99d7a1b99d7cfbde165d5ec39f5f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158944"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="46770-102">REF CURSOR Örnekleri</span><span class="sxs-lookup"><span data-stu-id="46770-102">REF CURSOR Examples</span></span>
<span data-ttu-id="46770-103">REF CURSOR örnekleri REF CURSOR kullanımını gösteren aşağıdaki üç Microsoft Visual Basic örnekleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="46770-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="46770-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="46770-104">Sample</span></span>|<span data-ttu-id="46770-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46770-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46770-106">OracleDataReader’da REF CURSOR Parametreleri</span><span class="sxs-lookup"><span data-stu-id="46770-106">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="46770-107">Bu örnekte REF CURSOR parametresiyle döndürür ve değeri olarak okuyan bir PL/SQL saklı yordamı yürüten bir <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="46770-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="46770-108">OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="46770-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="46770-109">Bu örnek iki REF CURSOR parametreleri döndürür ve kullanarak değerlerini okur PL/SQL saklı yordamı yürüten bir **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="46770-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="46770-110">Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="46770-110">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="46770-111">Bu örnek iki REF CURSOR parametreleri döndürür ve dolduran bir PL/SQL saklı yordamı yürüten bir <xref:System.Data.DataSet> satırlarla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="46770-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="46770-112">PL/SQL paketi ve paket gövdesi oluşturmanız gerekir ve bu örnekleri kullanmak için Oracle tablolar oluşturmak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="46770-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="46770-113">Oracle tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="46770-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="46770-114">Bu örnekler, Oracle Scott/Tiger şemasında tanımlanan tabloları kullanın.</span><span class="sxs-lookup"><span data-stu-id="46770-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="46770-115">Oracle Scott/Tiger şema çoğu Oracle yüklemeleri ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="46770-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="46770-116">Bu şema mevcut değilse SQL komutları dosyasında {OracleHome}\rdbms\admin\scott.sql. Bu örnek tarafından kullanılan dizinlerin ve tabloları oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46770-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="46770-117">Paket gövdesi ve Oracle paket oluşturma</span><span class="sxs-lookup"><span data-stu-id="46770-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="46770-118">Bu örnekler, aşağıdaki PL/SQL paketi ve paket gövdesi sunucunuzdaki gerektirir.</span><span class="sxs-lookup"><span data-stu-id="46770-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="46770-119">Oracle sunucu üzerinde aşağıdaki Oracle paketini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46770-119">Create the following Oracle package on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 <span data-ttu-id="46770-120">Aşağıdaki Oracle paket gövdesi, Oracle sunucusunda oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46770-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a><span data-ttu-id="46770-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46770-121">See also</span></span>

- [<span data-ttu-id="46770-122">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="46770-122">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)
- [<span data-ttu-id="46770-123">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="46770-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
