---
title: "Sorgu planı (varlık SQL) önbelleğe alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3b7a607d7bda72f1ce79405053f165e163c45386
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="query-plan-caching-entity-sql"></a>Sorgu planı (varlık SQL) önbelleğe alma
Sorgu yürütme denemesi yapıldığında, sorgu ardışık düzen tam sorgu önceden derlenmiş ve kullanılabilir olup olmadığını görmek için sorgu planı önbelleğini arar. Bu durumda, yeni bir tane oluşturmak yerine önbelleğe alınmış planı yeniden kullanır. Eşleşen bir sorgu planı önbelleğinde bulunmazsa, sorgu derlenmiş ve önbelleğe alınmış. Bir sorgu tarafından tanımlanan kendi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metin ve parametre koleksiyonu (adları ve türlerini). Tüm metin karşılaştırmaları büyük/küçük harfe duyarlıdır.  
  
## <a name="configuration"></a>Yapılandırma  
 Sorgu planı önbelleğe alma aracılığıyla yapılandırılabilir <xref:System.Data.EntityClient.EntityCommand>.  
  
 Etkinleştirmek veya sorgu planı aracılığıyla önbelleğe almayı devre dışı bırakmak için <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, bu özelliği ayarlamak `true` veya `false`. Plan olası tek tek dinamik sorgular için önbelleğe almayı devre dışı bırakılması daha sonra bir kez kullanılacak performansı artırır.  
  
 Sorgu planı aracılığıyla önbelleğe almayı etkinleştir <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Önerilen uygulama  
 Dinamik sorgular, genel kaçınılmalıdır. Aşağıdaki dinamik sorgu örnek SQL ekleme saldırılarına karşı savunmasız çünkü tüm doğrulama olmadan doğrudan kullanıcı girişini alır.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Dinamik olarak üretilen sorguları kullanırsanız, gereksiz bellek tüketimi yeniden başlatmasının önbellek girişlerini önlemek için sorgu planı önbelleğe almayı devre dışı bırakın.  
  
 Statik sorgulamaları önbelleğe alma ve sorguları Parametreli sorgu planı performans fayda sağlayabilir. Statik bir sorgunun bir örnek verilmiştir:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Sorgu planı önbelleğinin düzgün eşleştirilmesini sorgular için bunlar aşağıdaki gereksinimlerle uyumlu olması gerekir:  
  
-   Sorgu metni sabit bir desen, tercihen bir sabit dize veya bir kaynağı olmalıdır.  
  
-   <xref:System.Data.EntityClient.EntityParameter>veya <xref:System.Data.Objects.ObjectParameter> bir kullanıcı tarafından sağlanan değer geçirilmelidir her yerde kullanılmalıdır.  
  
 Gereksiz yere sorgu planı önbellek yuvalarında tüketen aşağıdaki sorgu desenlerine kaçınmanız gerekir:  
  
-   Metindeki büyük küçük harf yapılan değişiklikler.  
  
-   Beyaz alan yapılan değişiklikler.  
  
-   Değişmez değerler geçer.  
  
-   Metin açıklamaları içinde yapılan değişiklikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
