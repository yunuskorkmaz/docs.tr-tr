---
title: Sorgu planı önbelleğe alma (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: ca95f3aed5c092247a97bbfe5b0237a45b95ae16
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249292"
---
# <a name="query-plan-caching-entity-sql"></a>Sorgu planı önbelleğe alma (Entity SQL)
Sorgu yürütme girişimi yapıldığında sorgu işlem hattı, tam sorgunun zaten derlenmiş ve kullanılabilir olup olmadığını görmek için kendi sorgu planı önbelleğini arar. Bu durumda, yeni bir tane oluşturmak yerine önbelleğe alınmış planı yeniden kullanır. Sorgu planı önbelleğinde eşleşme bulunmazsa sorgu derlenir ve önbelleğe alınır. Bir sorgu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metni ve parametre koleksiyonuyla tanımlanır (adlar ve türler). Tüm metin karşılaştırmaları büyük/küçük harfe duyarlıdır.  
  
## <a name="configuration"></a>Yapılandırma  
 Sorgu planı önbelleğe alma, <xref:System.Data.EntityClient.EntityCommand>aracılığıyla yapılandırılabilir.  
  
 Sorgu planını önbelleğe almayı <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>etkinleştirmek veya devre dışı bırakmak için, bu özelliği veya `false`olarak `true` ayarlayın. Daha sonra çok fazla kullanılması olası dinamik sorgular için plan önbelleğe alma işlemi devre dışı bırakılıyor performansı geliştirir.  
  
 Sorgu planı önbelleğe almayı <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>' de etkinleştirebilirsiniz.  
  
## <a name="recommended-practice"></a>Önerilen uygulama  
 Dinamik sorgular, genel olarak kaçınılmalıdır. Aşağıdaki dinamik sorgu örneği SQL ekleme saldırılarına karşı savunmasız olduğundan, Kullanıcı girişini herhangi bir doğrulama olmadan doğrudan alır.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Dinamik olarak oluşturulan sorguları kullanıyorsanız, yeniden kullanılması olası olmayan önbellek girdileri için gereksiz bellek tüketimini önlemek üzere sorgu planı önbelleğe almayı devre dışı bırakmayı düşünün.  
  
 Statik sorgularda ve parametreli sorgularda sorgu planı önbelleğe alma, performans avantajları sağlayabilir. Statik sorguya bir örnek aşağıda verilmiştir:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Sorguların sorgu planı önbelleği tarafından düzgün şekilde eşleştirileceği için, aşağıdaki gereksinimlere uymaları gerekir:  
  
- Sorgu metni, tercihen sabit bir dize veya kaynak olmak üzere sabit bir model olmalıdır.  
  
- <xref:System.Data.EntityClient.EntityParameter>ya <xref:System.Data.Objects.ObjectParameter> da Kullanıcı tarafından sağlanan değerin geçirilmesi gereken her yerde kullanılmalıdır.  
  
 Sorgu planı önbelleğinde gereksiz yuva kullanan aşağıdaki sorgu desenlerinden kaçınmanız gerekir:  
  
- Metinde harf durumunu değiştirir.  
  
- Boşluk olarak değişir.  
  
- Değişmez değerler üzerindeki değişiklikler.  
  
- Açıklamaların içindeki metinde yapılan değişiklikler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
