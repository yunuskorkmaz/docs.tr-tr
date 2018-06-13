---
title: Sorgu planı (varlık SQL) önbelleğe alma
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 0e00d7f9382fca2af630a8e1d50a5cde5178da05
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762042"
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
  
-   <xref:System.Data.EntityClient.EntityParameter> veya <xref:System.Data.Objects.ObjectParameter> bir kullanıcı tarafından sağlanan değer geçirilmelidir her yerde kullanılmalıdır.  
  
 Gereksiz yere sorgu planı önbellek yuvalarında tüketen aşağıdaki sorgu desenlerine kaçınmanız gerekir:  
  
-   Metindeki büyük küçük harf yapılan değişiklikler.  
  
-   Beyaz alan yapılan değişiklikler.  
  
-   Değişmez değerler geçer.  
  
-   Metin açıklamaları içinde yapılan değişiklikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
