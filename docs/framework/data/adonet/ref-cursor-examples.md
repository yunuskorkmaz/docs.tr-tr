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
# <a name="ref-cursor-examples"></a>REF CURSOR Örnekleri
REF CURSOR örnekleri, REF CURSOR'lar kullanılarak gösteren aşağıdaki üç Microsoft Visual Basic örneğinden oluşmaktadır.  
  
|Örnek|Açıklama|  
|------------|-----------------|  
|[OracleDataReader’da REF CURSOR Parametreleri](ref-cursor-parameters-in-an-oracledatareader.md)|Bu örnek, REF CURSOR parametresi döndüren bir PL/SQL depolanan <xref:System.Data.OracleClient.OracleDataReader>yordamı yürütür ve değeri .|  
|[OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](retrieving-data-from-multiple-ref-cursors.md)|Bu örnek, iki REF CURSOR parametresini döndüren ve **OracleDataReader**kullanarak değerleri okuyan bir PL/SQL depolanan yordamı yürütür.|  
|[Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](filling-a-dataset-using-one-or-more-ref-cursors.md)|Bu örnek, iki REF CURSOR parametresini döndüren ve bir <xref:System.Data.DataSet> tanesini döndürülen satırlarla dolduran bir PL/SQL saklı yordamı yürütür.|  
  
 Bu örnekleri kullanmak için Oracle tablolarını oluşturmanız gerekebilir ve bir PL/SQL paketi ve paket gövdesi oluşturmanız gerekir.  
  
## <a name="creating-the-oracle-tables"></a>Oracle Tabloları Oluşturma  
 Bu örnekler, Oracle Scott/Tiger şemasında tanımlanan tabloları kullanır. Oracle Scott/Tiger şeması çoğu Oracle yüklemesiyle birlikte verilir. Bu şema yoksa, bu örnekler tarafından kullanılan tablo ve dizinleri oluşturmak için {OracleHome}\rdbms\admin\scott.sql'deki SQL komutları dosyasını kullanabilirsiniz.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Oracle Paket ve Paket Gövdesi Oluşturma  
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
