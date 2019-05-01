---
title: .NET için güvenli kodlama yönergeleri
ms.date: 06/28/2018
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a8f0dfc1a2b5e09722876b73281ed1d8b6334e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018651"
---
# <a name="secure-coding-guidelines"></a>Güvenli kodlama yönergeleri

Kanıt tabanlı güvenlik ve kod erişimi güvenliği güvenliği uygulamak için çok güçlü, açık mekanizmaları sağlar. Çoğu uygulama kodu, yalnızca .NET tarafından uygulanan altyapısı kullanabilirsiniz. Bazı durumlarda, uygulamaya özgü ek güvenlik güvenlik sistemini genişletmek veya yeni bir geçici yöntemleri kullanarak yerleşik gereklidir.

.NET kullanarak, izinleri ve diğer uygulama kodunuzda zorunlu, kötü amaçlı kod olmasını istemediğiniz bilgilerine erişme veya istenmeyen diğer eylemleri gerçekleştirmesini önlemek için engelleri erect. Ayrıca, güvenlik ve kullanılabilirlik arasında bir denge güvenilen kod kullanarak tüm beklenen senaryolarda strike gerekir.

Bu genel bakışta, kod güvenlik sistemiyle çalışacak şekilde tasarlanmış farklı yollarını açıklar.

## <a name="securing-resource-access"></a>Kaynak erişiminin güvenliğini sağlama

Tasarlama ve yazma kodunuzu koruyun ve kod özellikle kullanırken veya bilinmeyen kaynaklardan gelen kod yürütmesini kaynaklarına sahip olduğu erişimi sınırlamak gerekir. Bu nedenle, kodunuzu güvenli olduğundan emin olmak için aşağıdaki tekniklerden göz önünde bulundurun:

- Kod erişim güvenliği (CAS) kullanmayın.

- Kısmen güvenilen kod kullanmayın.

- Kullanmayın [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) özniteliği (APTCA).

- .NET uzaktan iletişim kullanmayın.

- Dağıtılmış Bileşen Nesne Modeli (DCOM) kullanmayın.

- İkili biçimlendiricileri kullanmayın.

Kod erişimi güvenliği ve güvenliği saydam kod kısmen güvenilen kod ile güvenlik sınırı olarak desteklenmez. Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez. Alternatif güvenlik önlemleri şunlardır:

- Sanallaştırma

- AppContainers

- İşletim sistemi (OS) kullanıcıları ve izinleri

- Hyper-V kapsayıcıları

## <a name="security-neutral-code"></a>Tarafsız güvenlik kodu

Tarafsız güvenlik kodu güvenlik sistemi ile açık bir şey yapmaz. Bu izinlere çalıştığı alır. (Örneğin, dosyalar, ağ vb. kullanarak) korumalı işlemleriyle ilişkili güvenlik özel durumları yakalamak için başarısız olan uygulamaları içinde işlenmeyen bir özel yol açabilir ancak Tarafsız güvenlik kodu yine de güvenlik teknolojilerini. NET'te yararlanır .

Tarafsız güvenlik kitaplığı anlamanız gereken özel özelliklere sahiptir. Kitaplığınızı dosyalarını kullanın ya da yönetilmeyen kod çağırmak API öğeleri sağlar varsayalım. Kodunuzu karşılık gelen izni yoksa, açıklandığı gibi çalışmaz. Ancak, kod izni olmasa bile, çağıran herhangi bir uygulama kodu çalışması için aynı izni olması gerekir. Çağıran kod doğru izne sahip değilse bir <xref:System.Security.SecurityException> sonucunda kod erişim güvenlik yığın ilerlemesi görüntülenir.

## <a name="application-code-that-isnt-a-reusable-component"></a>Yeniden kullanılabilir bir bileşen olmayan uygulama kodu

Kodunuzun diğer kod tarafından çağrılmak olmaz bir uygulamanın parçası ise, güvenlik basittir ve özel kodlama gerekli olmayabilir. Bununla birlikte, kötü amaçlı kod kodunuzu çağırabilirsiniz unutmayın. Kod erişimi güvenliği kaynaklara erişimini kötü amaçlı kod durdurabilir, ancak bu tür kod hala alanlar veya hassas bilgiler içerebilir özellikleri değerlerini okuyabilir.

Ayrıca, kodunuzu Internet'ten veya güvenilir olmayan diğer kaynaklardan kullanıcı girişi kabul ederse, kötü amaçlı girişi hakkında dikkatli olmalıdır.

## <a name="managed-wrapper-to-native-code-implementation"></a>Sarmalayıcı yerel kod uygulamasına yönetilen

Genellikle bu senaryoda, yönetilen kod için kullanılabilir hale getirmek istediğiniz yerel kodda bazı kullanışlı işlevsellik uygulanır. Yönetilen sarmalayıcılar, yazma ya da platform çağırma kullanma veya COM birlikte çalışma için kolaydır. Ancak bunu yaparsanız, sarmalayıcıları arayanlar başarılı olması için yönetilmeyen kod haklarına sahip olmalıdır. Varsayılan ilkesi altında bu kod intranetten indirilen veya Internet ile sarmalayıcıları çalışmaz anlamına gelir.

Bu sarmalayıcılar kullanan tüm uygulamalar için yönetilmeyen kod hakları vermek yerine, yalnızca sarmalayıcı kodu bu hakları vermek iyidir. Hiçbir kaynaklarını temel işlevselliği kullanıma sunar ve uygulama benzer şekilde güvenlidir, sarmalayıcı yalnızca kendi hakları assert içinden çağırmak herhangi bir kod sağlayan gerekir. Kaynaklar söz konusu olduğunda güvenlik kodlama sonraki bölümde açıklanan kitaplık kodu çalışması ile aynı olması gerekir. Sarmalayıcı çağıranlar bu kaynaklara potansiyel olarak kullanıma sunmak için yerel kod güvenliği dikkatli doğrulama gereklidir ve sarmalayıcının sorumluluğundadır.

## <a name="library-code-that-exposes-protected-resources"></a>Korunan kaynakları gösteren kitaplık kodu

En güçlü ve bu nedenle aşağıdaki yaklaşımı (yanlışlıkla yapıldıysa) tehlikeli güvenlik kodlamak için: .NET sınıfları yalnızca zorunlu olarak kullanamayacağınız, aksi takdirde, belirli kaynaklara erişmek başka bir kod için bir arabirimi kitaplığınızı görür kullandıkları kaynaklar için izinler. Bir kaynak kullanıma her yerde, kodunuzu kaynağa uygun izni ilk talep gerekir (diğer bir deyişle, bu güvenlik denetimi gerçekleştirmeniz gerekir) ve genellikle gerçek işlemi gerçekleştirme hakkı onay.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Durum Verilerinin Güvenliğini Sağlama](securing-state-data.md)|Özel üyeler korumak nasıl açıklar.|
|[Güvenlik ve Kullanıcı Girdisi](security-and-user-input.md)|Kullanıcı girişi kabul eden uygulamalar ile ilgili güvenlik konuları açıklanmaktadır.|
|[Güvenlik ve Yarış Durumları](security-and-race-conditions.md)|Yarış durumları kodunuzda önlemek nasıl açıklar.|
|[Güvenlik ve Çalışma Sırasında Kod Oluşturma](security-and-on-the-fly-code-generation.md)|Dinamik kod oluşturan uygulamalar ile ilgili güvenlik konuları açıklanmaktadır.|
|[Rol Tabanlı Güvenlik](role-based-security.md)|.NET rol tabanlı güvenlik ayrıntılı açıklar ve kodunuzda kullanma yönergeleri sağlar.|
