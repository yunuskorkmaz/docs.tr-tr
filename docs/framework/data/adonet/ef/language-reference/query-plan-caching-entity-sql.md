---
title: Sorgu planını önbelleğe alma (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 9f042d46d9a601c1091e36f8d81ce8f933140b20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178184"
---
# <a name="query-plan-caching-entity-sql"></a>Sorgu planını önbelleğe alma (varlık SQL)
Her bir sorgu yürütme girişimi yapıldığında, sorgu işlem hattındaki tam sorgu zaten derlenmiş ve kullanılabilir olup olmadığını görmek için sorgu planı önbelleği arar. Bu durumda, yeni bir tane oluşturmak yerine önbellekteki plan kullanır. Sorgu planı önbellekte bir eşleşme bulunmazsa, sorgu derlenmiş ve önbelleğe alınır. Bir sorgu tarafından tanımlanan kendi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metin ve parametre koleksiyonu (adlarını ve türlerini). Tüm metin karşılaştırmalar büyük/küçük harfe duyarlıdır.  
  
## <a name="configuration"></a>Yapılandırma  
 Sorgu planını önbelleğe alma aracılığıyla yapılandırılabilir <xref:System.Data.EntityClient.EntityCommand>.  
  
 Etkinleştirme veya devre dışı aracılığıyla sorgu planını önbelleğe alma <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, bu özelliği ayarlayın `true` veya `false`. Plan düşüktür bireysel dinamik sorgular için önbelleğe alma devre dışı bırakılması daha sonra bir kez kullanılacak performansını artırır.  
  
 Aracılığıyla sorgu planını önbelleğe alma etkinleştirebilirsiniz <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Önerilen uygulama  
 Dinamik sorgular, genellikle kaçınılmalıdır. Herhangi bir doğrulama olmadan doğrudan kullanıcı girişi aldığından aşağıdaki dinamik sorgu örnek SQL enjeksiyon saldırılarına karşı savunmasızdır.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Dinamik olarak üretilen sorguları kullanırsanız, gereksiz bellek tüketimi için kullanılabilmeleri düşüktür önbellek girişlerinin önlemek için sorgu planını önbelleğe alma devre dışı bırakmayı düşünün.  
  
 Statik sorguları önbelleğe alma ve sorgu parametreli bir sorgu planı performans avantajları sağlayabilir. Statik bir sorgu örneği verilmiştir:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Sorguların sorgu planı önbelleği tarafından düzgün şekilde eşlenmesi için aşağıdaki gereksinimlere uyması:  
  
-   Sorgu metni, sabit bir desen, tercihen bir sabit dize veya bir kaynak olmalıdır.  
  
-   <xref:System.Data.EntityClient.EntityParameter> veya <xref:System.Data.Objects.ObjectParameter> bir kullanıcı tarafından sağlanan değer geçirilen her yerde kullanılmalıdır.  
  
 Sorgu planını önbelleğe yuvalarda gereksiz yere kullanmak aşağıdaki sorgu desenleri kaçınmanız gerekir:  
  
-   Metindeki büyük küçük harf yapılan değişiklikler.  
  
-   Boşluk yapılan değişiklikler.  
  
-   Değişmez değerler geçer.  
  
-   Metin açıklama içinde yapılan değişiklikler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
