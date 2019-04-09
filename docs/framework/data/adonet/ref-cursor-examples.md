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
# <a name="ref-cursor-examples"></a>REF CURSOR Örnekleri
REF CURSOR örnekleri REF CURSOR kullanımını gösteren aşağıdaki üç Microsoft Visual Basic örnekleri oluşur.  
  
|Örnek|Açıklama|  
|------------|-----------------|  
|[OracleDataReader’da REF CURSOR Parametreleri](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|Bu örnekte REF CURSOR parametresiyle döndürür ve değeri olarak okuyan bir PL/SQL saklı yordamı yürüten bir <xref:System.Data.OracleClient.OracleDataReader>.|  
|[OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|Bu örnek iki REF CURSOR parametreleri döndürür ve kullanarak değerlerini okur PL/SQL saklı yordamı yürüten bir **OracleDataReader**.|  
|[Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|Bu örnek iki REF CURSOR parametreleri döndürür ve dolduran bir PL/SQL saklı yordamı yürüten bir <xref:System.Data.DataSet> satırlarla döndürülür.|  
  
 PL/SQL paketi ve paket gövdesi oluşturmanız gerekir ve bu örnekleri kullanmak için Oracle tablolar oluşturmak gerekebilir.  
  
## <a name="creating-the-oracle-tables"></a>Oracle tablo oluşturma  
 Bu örnekler, Oracle Scott/Tiger şemasında tanımlanan tabloları kullanın. Oracle Scott/Tiger şema çoğu Oracle yüklemeleri ile birlikte gelir. Bu şema mevcut değilse SQL komutları dosyasında {OracleHome}\rdbms\admin\scott.sql. Bu örnek tarafından kullanılan dizinlerin ve tabloları oluşturmak için kullanabilirsiniz.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Paket gövdesi ve Oracle paket oluşturma  
 Bu örnekler, aşağıdaki PL/SQL paketi ve paket gövdesi sunucunuzdaki gerektirir. Oracle sunucu üzerinde aşağıdaki Oracle paketini oluşturun.  
  
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
  
 Aşağıdaki Oracle paket gövdesi, Oracle sunucusunda oluşturun.  
  
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

- [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
