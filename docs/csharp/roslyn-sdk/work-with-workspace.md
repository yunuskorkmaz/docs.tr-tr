---
title: .NET Derleyici Platformu SDK çalışma alanı modeli ile çalışma
description: Bu genel bakış, kodunuz için çalışma alanını ve projeleri sorgulamak ve işlemek için kullandığınız türün anlaşılmasını sağlar.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: d21873b132d5f0788033693a319e556feeac59a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156889"
---
# <a name="work-with-a-workspace"></a>Bir çalışma alanı ile çalışma

**Çalışma Alanları** katmanı, kod çözümlemesi yapmak ve tüm çözümleri yeniden düzenlemek için başlangıç noktasıdır. Bu katman da, Çalışma Alanı API'si, çözümdeki projelerle ilgili tüm bilgileri tek bir nesne modeline dönüştürmenize yardımcı olarak kaynak metin, sözdizimi ağaçları, anlamsal modeller gibi derleyici katman nesne modellerine doğrudan erişim sağlar ve dosyaları ayrıştırmaya, seçenekleri yapılandırmaya veya projeler arası bağımlılıkları yönetmeye gerek kalmadan derlemeler.

IDE gibi ana bilgisayar ortamları, açık çözüme karşılık gelen bir çalışma alanı sağlar. Bu modeli bir IDE dışında yalnızca bir çözüm dosyası yükleyerek kullanmak da mümkündür.

## <a name="workspace"></a>Çalışma alanı

Çalışma alanı, çözümünüzün her biri belge koleksiyonuna sahip projeler topluluğu olarak etkin bir temsilidir. Çalışma alanı genellikle, kullanıcı türleri olarak sürekli değişen veya özellikleri manipüle eden bir ana bilgisayar ortamına bağlıdır.

Çözümün <xref:Microsoft.CodeAnalysis.Workspace> geçerli modeline erişim sağlar. Ana bilgisayar ortamında bir değişiklik olduğunda, çalışma alanı ilgili <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> olayları çalıştırıyor ve özellik güncelleştirilir. Örneğin, kullanıcı kaynak belgelerden birine karşılık gelen bir metin düzenleyicisinde yazdığında, çalışma alanı çözümün genel modelinin değiştiğini ve hangi belgenin değiştirildiğini bildirmek için bir olay kullanır. Daha sonra, yeni modeli doğruluk için çözümleyerek, önem alanlarını vurgulayarak veya kod değişikliği için bir öneride bulunarak bu değişikliklere tepki verebilirsiniz.

Ayrıca, ana bilgisayar ortamından bağlantısı kesilen veya ana bilgisayar ortamı olmayan bir uygulamada kullanılan bağımsız çalışma alanları da oluşturabilirsiniz.

## <a name="solutions-projects-documents"></a>Çözümler, projeler, belgeler

Bir anahtara her basıldığında çalışma alanı değişebilir, ancak çözüm modeliyle birlikte yalıtımda çalışabilirsiniz.

Çözüm, projelerin ve belgelerin değişmez bir modelidir. Bu, modelin kilitleme veya çoğaltma olmadan paylaşılabildiği anlamına gelir. <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> Özellikten bir çözüm örneği aldıktan sonra, bu örnek asla değişmez. Ancak, sözdizimi ağaçları ve derlemelerde olduğu gibi, varolan çözümleri ve belirli değişiklikleri temel alarak yeni örnekler oluşturarak çözümleri değiştirebilirsiniz. Çalışma alanının değişikliklerinizi yansıtmasını sağlamak için, değiştirilen çözümü açıkça çalışma alanına geri uygulamanız gerekir.

Proje, genel değişmez çözüm modelinin bir parçasıdır. Tüm kaynak kodu belgelerini, ayrıştırma ve derleme seçeneklerini ve hem derlemeyi hem de projeden projeye başvurularını temsil eder. Projeden, proje bağımlılıklarını belirlemenize veya kaynak dosyalarını ayrıştırmaya gerek kalmadan ilgili derlemeye erişebilirsiniz.

Belge aynı zamanda genel değişmez çözüm modelinin bir parçasıdır. Belge, dosyanın metnine, sözdizimi ağacına ve anlamsal modele erişebileceğiniz tek bir kaynak dosyayı temsil eder.

Aşağıdaki diyagram, Çalışma Alanı'nın ana bilgisayar ortamı, araçlar ve nasıl yapılan akışlarla ilişkili olduğunu gösterir.

![projeleri ve kaynak dosyaları içeren bir çalışma alanının farklı öğeleri arasındaki ilişkiler](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Özet

Roslyn, kaynak kodunuz hakkında zengin bilgiler sağlayan ve C# ve Visual Basic dilleriyle tam doğruluğu olan bir dizi derleyici API'sini ve Çalışma Alanı API'sini ortaya çıkarır.  .NET Derleyici Platformu SDK, kod odaklı araçlar ve uygulamalar oluşturmak için giriş engelini önemli ölçüde düşürür. Meta programlama, kod oluşturma ve dönüştürme, C# ve Visual Basic dillerinin etkileşimli kullanımı ve etki alanına özgü dillerde C# ve Visual Basic'in katıştırma gibi alanlarda inovasyon için birçok fırsat yaratır.  
