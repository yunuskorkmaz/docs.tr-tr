---
title: REF CURSOR Örnekleri
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: dc82648ff5a565c9b4d6fa593433ee1e22249d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149141"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="7002d-102">REF CURSOR Örnekleri</span><span class="sxs-lookup"><span data-stu-id="7002d-102">REF CURSOR Examples</span></span>
<span data-ttu-id="7002d-103">REF CURSOR örnekleri, REF CURSOR'lar kullanılarak gösteren aşağıdaki üç Microsoft Visual Basic örneğinden oluşmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7002d-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="7002d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7002d-104">Sample</span></span>|<span data-ttu-id="7002d-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7002d-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7002d-106">OracleDataReader’da REF CURSOR Parametreleri</span><span class="sxs-lookup"><span data-stu-id="7002d-106">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="7002d-107">Bu örnek, REF CURSOR parametresi döndüren bir PL/SQL depolanan <xref:System.Data.OracleClient.OracleDataReader>yordamı yürütür ve değeri .</span><span class="sxs-lookup"><span data-stu-id="7002d-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="7002d-108">OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="7002d-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="7002d-109">Bu örnek, iki REF CURSOR parametresini döndüren ve **OracleDataReader**kullanarak değerleri okuyan bir PL/SQL depolanan yordamı yürütür.</span><span class="sxs-lookup"><span data-stu-id="7002d-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="7002d-110">Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="7002d-110">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="7002d-111">Bu örnek, iki REF CURSOR parametresini döndüren ve bir <xref:System.Data.DataSet> tanesini döndürülen satırlarla dolduran bir PL/SQL saklı yordamı yürütür.</span><span class="sxs-lookup"><span data-stu-id="7002d-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="7002d-112">Bu örnekleri kullanmak için Oracle tablolarını oluşturmanız gerekebilir ve bir PL/SQL paketi ve paket gövdesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7002d-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="7002d-113">Oracle Tabloları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7002d-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="7002d-114">Bu örnekler, Oracle Scott/Tiger şemasında tanımlanan tabloları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7002d-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="7002d-115">Oracle Scott/Tiger şeması çoğu Oracle yüklemesiyle birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="7002d-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="7002d-116">Bu şema yoksa, bu örnekler tarafından kullanılan tablo ve dizinleri oluşturmak için {OracleHome}\rdbms\admin\scott.sql'deki SQL komutları dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7002d-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="7002d-117">Oracle Paket ve Paket Gövdesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7002d-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="7002d-118">Bu örnekler, sunucunuzda aşağıdaki PL/SQL paketini ve paket gövdesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7002d-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="7002d-119">Oracle sunucusunda aşağıdaki Oracle paketini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7002d-119">Create the following Oracle package on the Oracle server.</span></span>  
  
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
  
 <span data-ttu-id="7002d-120">Oracle sunucusunda aşağıdaki Oracle paket gövdesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7002d-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7002d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7002d-121">See also</span></span>

- [<span data-ttu-id="7002d-122">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7002d-122">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="7002d-123">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7002d-123">ADO.NET Overview</span></span>](ado-net-overview.md)
