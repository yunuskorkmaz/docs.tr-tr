---
title: Sorgu Planı Önbelleğe Alma (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: a0e84f40aed2cff146e4e203cca73a9110de0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149992"
---
# <a name="query-plan-caching-entity-sql"></a>Sorgu Planı Önbelleğe Alma (Entity SQL)
Sorguyu yürütme girişimi yapıldığında, sorgu ardışık lığı tam sorgunun zaten derlenip derlenmediğini ve kullanılabilir olup olmadığını görmek için sorgu planı önbelleğini arar. Bu öyleyse, yeni bir plan oluşturmak yerine önbelleğe alınmış planı yeniden kullanır. Sorgu planı önbelleğinde eşleşme bulunmazsa, sorgu derlenir ve önbelleğe çıkar. Sorgu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metin ve parametre koleksiyonu (adlar ve türleri) ile tanımlanır. Tüm metin karşılaştırmaları büyük/küçük harf duyarlıdır.  
  
## <a name="configuration"></a>Yapılandırma  
 Sorgu planı önbelleğe alma <xref:System.Data.EntityClient.EntityCommand>yoluyla yapılandırılabilir.  
  
 Sorgu planını etkinleştirmek veya devre <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>dışı kalım `true` sağlamak `false`için, bu özelliği veya ' ı ayarla Bir kez performansı artırır daha sonra daha fazla kullanılması olası değildir bireysel dinamik sorguları için plan önbelleğe alma.  
  
 Sorgu planı önbelleğe'yi <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>etkinleştirebilirsiniz.  
  
## <a name="recommended-practice"></a>Önerilen Uygulama  
 Genel olarak dinamik sorgulardan kaçınılmalıdır. Aşağıdaki dinamik sorgu örneği, kullanıcı girişini herhangi bir doğrulama olmadan doğrudan aldığından, SQL enjeksiyon saldırılarına karşı savunmasızdır.  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 Dinamik olarak oluşturulan sorgular kullanıyorsanız, yeniden kullanılma olasılığı düşük önbellek girişleri için gereksiz bellek tüketiminden kaçınmak için sorgu planı önbelleğe almamayı düşünün.  
  
 Statik sorgularda ve parametreli sorgularda önbelleğe alma sorgusu performansı avantajları sağlayabilir. Statik bir sorgu örneği aşağıda verilmiştir:  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Sorguların sorgu planı önbelleği tarafından düzgün bir şekilde eşleşebilmek için aşağıdaki gereksinimlere uymaları gerekir:  
  
- Sorgu metni sabit bir desen, tercihen sabit bir dize veya kaynak olmalıdır.  
  
- <xref:System.Data.EntityClient.EntityParameter>veya <xref:System.Data.Objects.ObjectParameter> kullanıcı tarafından sağlanan bir değerin geçirilmesi gereken her yerde kullanılmalıdır.  
  
 Sorgu planı önbelleğinde gereksiz yere yuva tüketen aşağıdaki sorgu desenlerinden kaçınmalısınız:  
  
- Metindeki harf örneğinde değişiklikler.  
  
- Beyaz boşlukta değişiklikler.  
  
- Gerçek değerlerde değişiklikler.  
  
- Açıklamaların içindeki metinde yapılan değişiklikler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
