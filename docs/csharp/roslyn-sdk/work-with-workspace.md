---
title: .NET Compiler Platform SDK çalışma alanı modeliyle çalışma
description: Bu genel bakışta, kodunuzun çalışma alanını ve projelerini sorgulamak ve işlemek için kullandığınız tür hakkında bilgi sağlanır.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: b613c85c01cc054dea9dd4bb9cf0062ffedb08bf
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899119"
---
# <a name="work-with-a-workspace"></a>Bir çalışma alanı ile çalışma

**Çalışma alanları** katmanı, Kod analizini yapmak ve çözümlerin tamamında yeniden düzenleme yapmak için başlangıç noktasıdır. Bu katman içinde, çalışma alanı API 'SI, bir çözümdeki projelerle ilgili tüm bilgileri tek bir nesne modelinde organize ediyor ve böylece dosya ayrıştırmaya, seçenekleri yapılandırmanıza veya proje içi bağımlılıkları yönetmeye gerek kalmadan kaynak metin, sözdizimi ağaçları, anlam modelleri ve derlemeler gibi derleyici katmanı nesne modellerine doğrudan erişim imkanı sunar.

IDE gibi ana bilgisayar ortamları, açık çözüme karşılık gelen sizin için bir çalışma alanı sağlar. Ayrıca, bir çözüm dosyası yükleyerek bu modelin IDE dışında kullanılması da mümkündür.

## <a name="workspace"></a>Çalışma alanı

Çalışma alanı, çözümünüzün bir proje koleksiyonu olarak, her biri bir belge koleksiyonu olarak etkin bir gösterimidir. Çalışma alanı, genellikle kullanıcı türleri olarak değişen veya özellikleri işleyen bir konak ortamına bağlıdır.

, <xref:Microsoft.CodeAnalysis.Workspace> Çözümün geçerli modeline erişim sağlar. Konak ortamında değişiklik yapıldığında, çalışma alanı ilgili olayları harekete geçirilir ve <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> özellik güncellenir. Örneğin, Kullanıcı, kaynak belgelerden birine karşılık gelen bir metin düzenleyicisinde yazdığında, çalışma alanı, çözümün genel modelinin değiştiğini ve hangi belgenin değiştirildiğini işaret etmek için bir olay kullanır. Daha sonra bu değişikliklere, yeni modeli doğru şekilde çözümleyerek, anlamlı alanların vurgulanmasını veya bir kod değişikliği önerisi yapmayı sağlayabilirsiniz.

Konak ortamından bağlantısı kesilen veya konak ortamı olmayan bir uygulamada kullanılan tek başına çalışma alanları da oluşturabilirsiniz.

## <a name="solutions-projects-and-documents"></a>Çözümler, projeler ve belgeler

Bir anahtara her basıldığında bir çalışma alanı değişebilir, ancak çözüm modeliyle, yalıtım halinde çalışabilirsiniz.

Çözüm, proje ve belgelerin sabit bir modelidir. Bu, modelin kilitleme veya çoğaltma olmadan paylaşılabilecek anlamına gelir. Özellikten bir çözüm örneği elde ettikten sonra <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> , bu örnek hiçbir şekilde değişmez. Ancak, söz dizimi ağaçları ve derlemeler gibi, mevcut çözümlere ve belirli değişikliklere göre yeni örnekler oluşturarak çözümleri değiştirebilirsiniz. Çalışma alanını değişikliklerinizi yansıtacak şekilde almak için, değiştirilen çözümü çalışma alanına geri uygulamanız gerekir.

Proje, genel olarak sabit çözüm modelinin bir parçasıdır. Tüm kaynak kodu belgelerini, ayrıştırmasını ve derleme seçeneklerini ve hem derleme hem de projeden projeye başvuruları temsil eder. Bir projeden, Proje bağımlılıklarını belirleme veya herhangi bir kaynak dosyayı ayrıştırmaya gerek kalmadan ilgili derlemeye erişebilirsiniz.

Belge ayrıca, genel sabit çözüm modelinin bir parçasıdır. Belge, dosyanın metnine, sözdizimi ağacına ve anlam modeline erişebileceğiniz tek bir kaynak dosyayı temsil eder.

Aşağıdaki diyagram, çalışma alanının ana bilgisayar ortamı, araçları ve düzenlemelerle nasıl ilişkili olduğunu gösteren bir gösterimidir.

![projeleri ve kaynak dosyaları içeren bir çalışma alanının farklı öğeleri arasındaki ilişkiler](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Özet

Roslyn, kaynak kodunuz hakkında zengin bilgi sağlayan ve C# ve Visual Basic dilleri ile tam uygunluğu olan bir derleyici API 'si ve çalışma alanı API 'Leri kümesi sunar.  .NET Compiler Platform SDK, kod odaklı araçları ve uygulamaları oluşturmak için engel önemli ölçüde düşürür. Meta programlama, kod oluşturma ve dönüştürme, C# ve Visual Basic dillerinin etkileşimli kullanımı ve etki alanına özgü dillerde C# ve Visual Basic ekleme gibi alanlarda yenilik için birçok fırsat oluşturur.  
