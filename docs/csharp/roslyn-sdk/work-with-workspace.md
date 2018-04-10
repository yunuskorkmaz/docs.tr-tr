---
title: .NET derleme Platform SDK çalışma modeli ile çalışmak
description: Bu genel bakışta, sorgu ve çalışma ve projeler için kodunuzu değiştirmek için kullandığınız türünün bir anlayış sağlar.
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: c42795346c505f925c0b4cb232325085fa065201
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="work-with-a-workspace"></a>Bir çalışma alanı ile çalışma

**Çalışma alanları** katman için kod analizi yapmak ve tüm çözümleri yeniden düzenleme başlangıç noktasıdır. Bu katman içinde çalışma API, bir çözümde proje ilgili tüm bilgileri tek nesne modeline düzenleme içinde kaynak metni, sözdizimi ağaçları, semantik modellerin gibi derleyici katman nesnesi modellerini doğrudan erişim sunan yardımcı olur ve dosyaları ayrıştırma gerek olmadan derlemeleri seçeneklerini yapılandırmak veya arası proje bağımlılıkları yönetin. 

Bir IDE gibi ana bilgisayar ortamları, açık çözüme karşılık gelen bir çalışma alanı sağlar. Çözüm dosyası yükleyerek bu modeli bir IDE dışında kullanmak da mümkündür.

## <a name="workspace"></a>Çalışma alanı

Bir çalışma alanı bir active çözümünüzü koleksiyonu olarak projeleri, her bir koleksiyon belgelerin gösterimidir. Bir çalışma alanı genellikle bir kullanıcı türleri olarak sürekli değişen veya özellikler işleyen bir ana bilgisayar ortamı bağlıdır. 

<xref:Microsoft.CodeAnalysis.Workspace> Çözümün geçerli modeline erişim sağlar. Konak ortamında değişiklik olduğunda, ilgili olaylar çalışma başlatılır ve <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> özelliği güncelleştirilir. Örneğin, kullanıcı türleri kaynak belgeleri birine karşılık gelen bir metin düzenleyicisinde çalışma çözümünün Genel modeli değişti göstermek için bir olay ve hangi belgenin değiştirildiği kullandığında. Ardından, yeni modelin doğruluğunu çözümleme, anlamlı alanları vurgulama veya bir öneride bir kod değişikliği için bu değişiklikleri tepki gösterebilmesi. 

Hiçbir konak ortamında olan bir uygulama içinde kullanılan veya ana bilgisayar ortamına bağlı olmayan tek başına çalışma alanları da oluşturabilirsiniz.

## <a name="solutions-projects-documents"></a>Çözümler, projeler, belgeleri

Bir tuşa her zaman bir çalışma alanı değişebilir rağmen yalıtım çözümde modelinin çalışabilirsiniz. 

Bir çözüm, projeler ve belgeleri değişmez bir modelidir. Bu model kilitleme veya çoğaltma paylaşılabilir anlamına gelir. Bir çözüm örneğinden edindikten sonra <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> özelliği, bu örnek hiçbir zaman değişiklik gösterir. Ancak, gibi sözdizimi ağaçları ve derlemeleri, çözümleri var olan çözümler ve belirli değişiklikleri dayalı yeni kopyalarını oluşturarak değiştirebilirsiniz. Yaptığınız değişiklikleri yansıtacak şekilde çalışma alma çalışma alanına değiştirilen çözüm açıkça uygulamanız gerekir.

Bir proje genel değişmez çözüm modeli, bir parçasıdır. Tüm kaynak kodu belgeleri, ayrıştırma ve derleme seçenekleri ve hem derleme ve proje proje başvuruları temsil eder. Bir projeden proje bağımlılıkları belirlemek ya da tüm kaynak dosyaları ayrıştırma gerek kalmadan karşılık gelen derleme erişebilir.

Bir belge ayrıca genel değişmez çözüm modeli parçasıdır. Belgeye metin dosyası, sözdizimi ağacı ve anlam modeli erişmek için tek bir kaynak dosyası temsil eder.

Aşağıdaki diyagramda çalışma konağa ilişkilendirilme şekli gösterimidir ortamı, Araçlar ve düzenlemeler nasıl yapılır.

![Projeler ve kaynak dosyaları içeren bir çalışma alanının farklı öğeler arasındaki ilişkileri](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Özet

Roslyn bir dizi derleyici API'leri ve çalışma alanları, kaynak kodu hakkında zengin bilgi sağlayan ve C# ve Visual Basic dili ile tam uygunluğunu sahip API'lerini kullanıma sunar.  .NET derleme Platform SDK'sı kod odaklı araçları ve uygulamaları oluşturmak için girişe engel önemli ölçüde azaltır. C# ve VB diller ve C# ve VB etki alanı belirli dillerde katıştırma meta programlama kodu oluşturma ve dönüştürme, etkileşimli kullanımı gibi alanlarda yenilik için birçok fırsatlar yaratır.  
