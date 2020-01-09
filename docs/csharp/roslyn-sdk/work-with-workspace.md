---
title: .NET Compiler Platform SDK çalışma alanı modeliyle çalışma
description: Bu genel bakışta, kodunuzun çalışma alanını ve projelerini sorgulamak ve işlemek için kullandığınız tür hakkında bilgi sağlanır.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: a2e69129a869707eaec3516310a72f1fc918ca26
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346918"
---
# <a name="work-with-a-workspace"></a>Bir çalışma alanı ile çalışma

**Çalışma alanları** katmanı, Kod analizini yapmak ve çözümlerin tamamında yeniden düzenleme yapmak için başlangıç noktasıdır. Bu katman içinde, çalışma alanı API 'SI bir çözümdeki projelerle ilgili tüm bilgileri tek bir nesne modelinde organize ediyor ve böylece kaynak metin, sözdizimi ağaçları, anlam modelleri gibi derleyici katmanı nesne modellerine doğrudan erişim imkanı sunar. dosyaları ayrıştırmaya, seçenekleri yapılandırmaya veya proje dışı bağımlılıkları yönetmeye gerek kalmadan derlemeler. 

IDE gibi ana bilgisayar ortamları, açık çözüme karşılık gelen sizin için bir çalışma alanı sağlar. Ayrıca, bir çözüm dosyası yükleyerek bu modelin IDE dışında kullanılması da mümkündür.

## <a name="workspace"></a>Çalışma alanı

Çalışma alanı, çözümünüzün bir proje koleksiyonu olarak, her biri bir belge koleksiyonu olarak etkin bir gösterimidir. Çalışma alanı, genellikle kullanıcı türleri olarak değişen veya özellikleri işleyen bir konak ortamına bağlıdır. 

<xref:Microsoft.CodeAnalysis.Workspace> çözümün geçerli modeline erişim sağlar. Konak ortamında değişiklik yapıldığında, çalışma alanı ilgili olayları harekete geçirilir ve <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> özelliği güncellenir. Örneğin, Kullanıcı, kaynak belgelerden birine karşılık gelen bir metin düzenleyicisinde yazdığında, çalışma alanı, çözümün genel modelinin değiştiğini ve hangi belgenin değiştirildiğini işaret etmek için bir olay kullanır. Daha sonra bu değişikliklere, yeni modeli doğru şekilde çözümleyerek, anlamlı alanların vurgulanmasını veya bir kod değişikliği önerisi yapmayı sağlayabilirsiniz. 

Konak ortamından bağlantısı kesilen veya konak ortamı olmayan bir uygulamada kullanılan tek başına çalışma alanları da oluşturabilirsiniz.

## <a name="solutions-projects-documents"></a>Çözümler, projeler, belgeler

Bir anahtara her basıldığında bir çalışma alanı değişebilir, ancak çözüm modeliyle, yalıtım halinde çalışabilirsiniz. 

Çözüm, proje ve belgelerin sabit bir modelidir. Bu, modelin kilitleme veya çoğaltma olmadan paylaşılabilecek anlamına gelir. <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> özelliğinden bir çözüm örneği elde ettikten sonra, bu örnek hiçbir şekilde değişmeyecektir. Ancak, söz dizimi ağaçları ve derlemeler gibi, mevcut çözümlere ve belirli değişikliklere göre yeni örnekler oluşturarak çözümleri değiştirebilirsiniz. Çalışma alanını değişikliklerinizi yansıtacak şekilde almak için, değiştirilen çözümü çalışma alanına geri uygulamanız gerekir.

Proje, genel olarak sabit çözüm modelinin bir parçasıdır. Tüm kaynak kodu belgelerini, ayrıştırmasını ve derleme seçeneklerini ve hem derleme hem de projeden projeye başvuruları temsil eder. Bir projeden, Proje bağımlılıklarını belirleme veya herhangi bir kaynak dosyayı ayrıştırmaya gerek kalmadan ilgili derlemeye erişebilirsiniz.

Belge ayrıca, genel sabit çözüm modelinin bir parçasıdır. Belge, dosyanın metnine, sözdizimi ağacına ve anlam modeline erişebileceğiniz tek bir kaynak dosyayı temsil eder.

Aşağıdaki diyagram, çalışma alanının ana bilgisayar ortamı, araçları ve düzenlemelerle nasıl ilişkili olduğunu gösteren bir gösterimidir.

![projeleri ve kaynak dosyaları içeren bir çalışma alanının farklı öğeleri arasındaki ilişkiler](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Özet

Roslyn, C# kaynak kodunuz hakkında zengin bilgi sağlayan ve ve Visual Basic dilleri ile tam uygunluğa sahip olan bir derleyici API 'Si ve çalışma alanı API 'leri kümesi sunar.  .NET Compiler Platform SDK, kod odaklı araçları ve uygulamaları oluşturmak için engel önemli ölçüde düşürür. Meta programlama, kod oluşturma ve dönüştürme, C# ve Visual Basic dillerin etkileşimli kullanımı ve etki alanına özgü dillerde ekleme C# ve Visual Basic gibi alanlarda yenilik için birçok fırsat oluşturur.  
