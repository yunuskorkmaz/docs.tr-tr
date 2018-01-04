---
title: "REF İMLEÇ örnekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a672125dee4203e54d68cc8e19915f70f17fe915
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ref-cursor-examples"></a>REF İMLEÇ örnekleri
REF CURSOR örnekler REF imleçler kullanarak gösteren aşağıdaki üç Microsoft Visual Basic örnekleri oluşur.  
  
|Örnek|Açıklama|  
|------------|-----------------|  
|[OracleDataReader’da REF CURSOR Parametreleri](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|Bu örnek değeri olarak okur ve REF CURSOR parametresiyle döndüren bir PL/SQL saklı yordamı yürüten bir <xref:System.Data.OracleClient.OracleDataReader>.|  
|[OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|Bu örnek kullanılarak değerleri okur ve iki REF İMLEÇ parametreleri döndüren bir PL/SQL saklı yordamı yürüten bir **OracleDataReader**.|  
|[Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|Bu örnek doldurur ve iki REF İMLEÇ parametreleri döndüren bir PL/SQL saklı yordamı yürütür bir <xref:System.Data.DataSet> satırlarla döndürülür.|  
  
 Bu örnekleri kullanmak için Oracle tablolar oluşturmak gerekebilir ve PL/SQL paket ve paket gövdesi oluşturmanız gerekir.  
  
## <a name="creating-the-oracle-tables"></a>Oracle tabloları oluşturma  
 Bu örnekler Oracle Scott/Tiger şemada tanımlanan tabloları kullanın. Oracle Scott/Tiger şema çoğu Oracle yüklemeleriyle dahil edilir. Bu şemayı mevcut değilse, {tabloları ve bu örnekleri tarafından kullanılan dizinlerin OracleHome}\rdbms\admin\scott.sql. SQL komutlarını dosyasında kullanabilirsiniz  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Paket gövdesi ve Oracle paket oluşturma  
 Bu örnekler, aşağıdaki PL/SQL paketi ve paket gövdesi sunucunuzda gerektirir. Aşağıdaki Oracle paket Oracle sunucuda oluşturun.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 Aşağıdaki Oracle paket gövdesi Oracle sunucusunda oluşturun.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
