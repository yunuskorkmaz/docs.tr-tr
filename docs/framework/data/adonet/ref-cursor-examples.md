---
description: 'Daha fazla bilgi edinin: REF CURSOR örnekleri'
title: REF CURSOR Örnekleri
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: e7cb411778b325400d37511b082032e590b339c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773231"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="43161-103">REF CURSOR Örnekleri</span><span class="sxs-lookup"><span data-stu-id="43161-103">REF CURSOR Examples</span></span>

<span data-ttu-id="43161-104">REF CURSOR örnekleri, REF IMLEÇLER kullanmayı gösteren aşağıdaki üç Microsoft Visual Basic örneklerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="43161-104">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="43161-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="43161-105">Sample</span></span>|<span data-ttu-id="43161-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43161-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43161-107">OracleDataReader’da REF CURSOR Parametreleri</span><span class="sxs-lookup"><span data-stu-id="43161-107">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="43161-108">Bu örnek, bir REF CURSOR parametresi döndüren bir PL/SQL saklı yordamını yürütür ve değeri olarak okur <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="43161-108">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="43161-109">OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="43161-109">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="43161-110">Bu örnek, iki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamını yürütür ve bir **OracleDataReader** kullanarak değerleri okur.</span><span class="sxs-lookup"><span data-stu-id="43161-110">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="43161-111">Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="43161-111">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="43161-112">Bu örnek, iki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamını yürütür ve <xref:System.Data.DataSet> döndürülen satırlarla birlikte bir doldurur.</span><span class="sxs-lookup"><span data-stu-id="43161-112">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="43161-113">Bu örnekleri kullanmak için Oracle tabloları oluşturmanız gerekebilir ve bir PL/SQL paketi ve paket gövdesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43161-113">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="43161-114">Oracle tabloları oluşturma</span><span class="sxs-lookup"><span data-stu-id="43161-114">Creating the Oracle Tables</span></span>  

 <span data-ttu-id="43161-115">Bu örnekler, Oracle Scott/Tiger şemasında tanımlanan tabloları kullanır.</span><span class="sxs-lookup"><span data-stu-id="43161-115">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="43161-116">Oracle Scott/Tiger şeması, çoğu Oracle yüklemelerine dahildir.</span><span class="sxs-lookup"><span data-stu-id="43161-116">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="43161-117">Bu şema yoksa, bu örneklerde kullanılan tabloları ve dizinleri oluşturmak için {OracleHome} \rdbms\admin\scott.SQL içindeki SQL komut dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43161-117">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="43161-118">Oracle paketi ve paket gövdesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="43161-118">Creating the Oracle Package and Package Body</span></span>  

 <span data-ttu-id="43161-119">Bu örnekler, sunucunuzda aşağıdaki PL/SQL paketini ve paket gövdesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43161-119">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="43161-120">Oracle sunucusunda aşağıdaki Oracle paketini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43161-120">Create the following Oracle package on the Oracle server.</span></span>  
  
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
  
 <span data-ttu-id="43161-121">Oracle sunucusunda aşağıdaki Oracle paket gövdesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43161-121">Create the following Oracle package body on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43161-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43161-122">See also</span></span>

- [<span data-ttu-id="43161-123">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="43161-123">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="43161-124">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="43161-124">ADO.NET Overview</span></span>](ado-net-overview.md)
