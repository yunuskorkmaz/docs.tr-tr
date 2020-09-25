---
title: REF CURSOR Örnekleri
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: b45ef971ccb6b785988cc351d02be9e0844f6e11
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200543"
---
# <a name="ref-cursor-examples"></a>REF CURSOR Örnekleri

REF CURSOR örnekleri, REF IMLEÇLER kullanmayı gösteren aşağıdaki üç Microsoft Visual Basic örneklerinden oluşur.  
  
|Örnek|Açıklama|  
|------------|-----------------|  
|[OracleDataReader’da REF CURSOR Parametreleri](ref-cursor-parameters-in-an-oracledatareader.md)|Bu örnek, bir REF CURSOR parametresi döndüren bir PL/SQL saklı yordamını yürütür ve değeri olarak okur <xref:System.Data.OracleClient.OracleDataReader> .|  
|[OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](retrieving-data-from-multiple-ref-cursors.md)|Bu örnek, iki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamını yürütür ve bir **OracleDataReader**kullanarak değerleri okur.|  
|[Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](filling-a-dataset-using-one-or-more-ref-cursors.md)|Bu örnek, iki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamını yürütür ve <xref:System.Data.DataSet> döndürülen satırlarla birlikte bir doldurur.|  
  
 Bu örnekleri kullanmak için Oracle tabloları oluşturmanız gerekebilir ve bir PL/SQL paketi ve paket gövdesi oluşturmanız gerekir.  
  
## <a name="creating-the-oracle-tables"></a>Oracle tabloları oluşturma  

 Bu örnekler, Oracle Scott/Tiger şemasında tanımlanan tabloları kullanır. Oracle Scott/Tiger şeması, çoğu Oracle yüklemelerine dahildir. Bu şema yoksa, bu örneklerde kullanılan tabloları ve dizinleri oluşturmak için {OracleHome} \rdbms\admin\scott.SQL içindeki SQL komut dosyasını kullanabilirsiniz.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Oracle paketi ve paket gövdesi oluşturma  

 Bu örnekler, sunucunuzda aşağıdaki PL/SQL paketini ve paket gövdesini gerektirir. Oracle sunucusunda aşağıdaki Oracle paketini oluşturun.  
  
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
  
 Oracle sunucusunda aşağıdaki Oracle paket gövdesini oluşturun.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle REF CURSOR](oracle-ref-cursors.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
