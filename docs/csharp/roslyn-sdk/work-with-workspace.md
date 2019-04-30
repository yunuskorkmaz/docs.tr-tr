---
title: .NET derleyici Platformu SDK'sı çalışma modeli ile çalışma
description: Bu genel bakışta çalışma alanını ve kodunuzu projelerde sorgulama ve düzenleme kullandığınız türünün bir anlayış sağlar.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 7d450b31cbf2c83c79552d1ace3a1ae692bfdd88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706510"
---
# <a name="work-with-a-workspace"></a>Bir çalışma alanı ile çalışma

**Çalışma alanları** katman tüm çözümleri yeniden düzenleme ve kod analizi yapmak için başlangıç noktasıdır. Bu katman içinde çalışma API, bir çözüm içindeki projeleri hakkındaki tüm bilgileri tek nesne modeline, düzenleme kaynak metni, söz dizimi ağacı, anlam modelleri gibi derleyici katman nesnesi modellerini doğrudan erişim sunan yardımcı olur ve dosyaları ayrıştırma gerek olmadan derleme seçenekleri yapılandırın veya Projeler arası bağımlılıkları yönetin. 

Bir IDE gibi konak ortamlarından, açık olan çözüme karşılık gelen bir çalışma alanı sağlayın. Bu model bir IDE dışında bir çözüm dosyası yükleyerek kullanmak mümkündür.

## <a name="workspace"></a>Çalışma alanı

Çözümünüzün proje koleksiyonu, her bir belge koleksiyonu olarak etkin bir temsili bir çalışma alanıdır. Bir çalışma alanı, genellikle bir kullanıcı türleri olarak sürekli değişen veya özellikleri işleyen bir ana bilgisayar ortamına bağlıdır. 

<xref:Microsoft.CodeAnalysis.Workspace> Geçerli çözüm modeline erişim sağlar. Konak ortamında değişiklik olduğunda, ilgili olaylar, çalışma alanı tetikler ve <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> özellik güncelleştirilir. Örneğin, kullanıcı türleri kaynak belgeleri birine karşılık gelen bir metin düzenleyicisinde çalışma çözümünün Genel modeli değiştiğini göstermek için bir olay ve hangi belge değiştirildiği kullandığında. Ardından, yeni modelin doğruluğunu çözümleme, alanlarını anlam vurgulama veya bir öneri bir kod değişikliği yapmadan bu değişiklikleri tepki verebilir. 

Ayrıca, konak ortam bir uygulamada kullanılan veya ana bilgisayar ortamına bağlı olmayan tek başına çalışma alanları oluşturabilirsiniz.

## <a name="solutions-projects-documents"></a>Çözümler, projeler, belgeleri

Bir çalışma alanında bir tuşa basıldığında her zaman değişebilir olsa da, yalıtım çözümde modelini çalışabilirsiniz. 

Bir çözümü, projeleri ve belgeleri değişmez bir modeldir. Bu model çoğaltma kilitlenmesi veya paylaşılabilir anlamına gelir. Bir çözüm örneğinden edindikten sonra <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> özelliği, bu örneği hiçbir zaman değiştirir. Ancak, gibi söz dizimi ağacı ve derlemeleri, ile çözümlerini mevcut çözümleri ve belirli değişiklikleri dayalı yeni örneklerini oluşturarak değiştirebilirsiniz. Yaptığınız değişiklikleri yansıtacak şekilde çalışma almak için açıkça değiştirilen çözümü çalışma alanına uygulamanız gerekir.

Bir proje, genel sabit çözüm modelin bir parçasıdır. Tüm kaynak kod belgelerini, ayrıştırma ve derleme seçeneklerini ve hem derleme ve projeden projeye başvurular temsil eder. Bir projeden karşılık gelen derleme proje bağımlılıkları belirlemeniz veya tüm kaynak dosyalarını ayrıştırmak gerek kalmadan erişebilir.

Bir belge ayrıca genel sabit çözüm modelin bir parçasıdır. Bir belge metin dosyası, söz dizimi ağacı ve anlam modeli erişim bir tek bir kaynak dosyasını temsil eder.

Aşağıdaki şemada çalışma konağa ilişkisini temsilidir ortamı, araçları ve düzenlemeleri nasıl yapılır.

![projeleri ve kaynak dosyaları içeren bir çalışma alanının farklı öğeler arasındaki ilişkileri](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Özet

Roslyn derleyici API'leri ve çalışma alanları tam uygunlukta sahip olan ve kaynak kodunuz hakkında zengin bilgiler sağlayan API kümesi sunan C# ve Visual Basic dillerini.  .NET derleyici Platformu SDK'sı, kod odaklı bir araç ve uygulamalar oluşturmak için giriş engel önemli ölçüde azaltır. C# ve VB dil ve C# ve VB etki alanına özgü diller katıştırma meta programlama kod oluşturma ve dönüştürme, etkileşimli kullanmak gibi alanlarda yenilik için birçok fırsat oluşturur.  
