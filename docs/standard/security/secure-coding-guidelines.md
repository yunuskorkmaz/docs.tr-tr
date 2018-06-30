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
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106742"
---
# <a name="secure-coding-guidelines"></a>Güvenli kodlama yönergeleri

Kanıt tabanlı güvenlik ve kod erişim güvenliği güvenlik uygulamak çok güçlü, açık mekanizmaları sağlar. Çoğu uygulama kodu yalnızca .NET tarafından uygulanan altyapısını kullanabilir. Bazı durumlarda, ek uygulamaya özgü güvenlik güvenlik sistemini genişletme veya yeni geçici yöntemleri kullanarak yerleşik gereklidir.

.NET kullanarak izinleri ve diğer uygulama kodunuzda zorlanan, olmasını istemediğiniz bilgiler erişmesini veya istenmeyen diğer eylemler gerçekleştiriyorsa kötü amaçlı kod önlemek için engelleri erect. Ayrıca, güvenlik ve kullanılabilirlik arasında bir denge güvenilen kod kullanarak tüm beklenen senaryolarda üstünü gerekir.

Bu genel bakışta kodu güvenlik sistemi ile çalışmak için tasarlanmış farklı yolları açıklanmaktadır.

## <a name="securing-resource-access"></a>Kaynak erişimini güvenli hale getirme

Tasarlama ve kodunuzu yazmaya korumak ve özellikle kullanırken veya bilinmeyen kod yürütmesini kaynaklarına koduna sahip erişimi sınırlamak gerekir. Bu nedenle, kodunuzu güvenli olduğundan emin olmak için aşağıdaki teknikleri göz önünde bulundurun:

- Kod erişim güvenliği (CAS) kullanmayın.

- Kısmen güvenilen kod kullanmayın.

- Kullanmayın [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) özniteliği (APTCA).

- .NET uzaktan iletişim kullanmayın.

- Dağıtılmış Bileşen Nesne Modeli (DCOM) kullanmayın.

- İkili biçimlendiricileri kullanmayın.

Kod erişimi güvenliği ve güvenliği saydam kod güvenlik sınırı kısmen güvenilen kodla desteklenmez. Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez. Alternatif güvenlik önlemleri şunlardır:

- Sanallaştırma

- AppContainers

- İşletim sistemi (OS) kullanıcılar ve izinler

- Hyper-V kapsayıcıları

## <a name="security-neutral-code"></a>Tarafsız güvenlik kodu

Tarafsız güvenlik kodu bir güvenlik sistemi açık hiçbir şey yapmaz. Hangi izinlerle onu çalıştırır alır. Korumalı işlemleri (örneğin, dosya, ağ vb. kullanarak) ile ilişkili güvenlik özel durumları yakalamak için başarısız uygulamaları içinde işlenmeyen bir özel yol açabilecek olsa da Tarafsız güvenlik kodu hala güvenlik teknolojileri .NET yararlanır .

Tarafsız güvenlik kitaplığı anlamanız gereken özel özelliklere sahiptir. Kitaplık dosyaları kullanan veya yönetilmeyen kodu çağırma API öğeleri sağlar varsayalım. Kodunuzu karşılık gelen izni yoksa, açıklandığı gibi çalışmaz. Bununla birlikte, kod izni olsa bile, çağıran herhangi bir uygulama kodu çalışması için aynı izni olmalıdır. Çağrıyı yapan kod sağ izni yoksa, bir <xref:System.Security.SecurityException> sonucunda kod erişim güvenliği yığın ilerlemesi görüntülenir.

## <a name="application-code-that-isnt-a-reusable-component"></a>Yeniden kullanılabilir bileşen olmayan uygulama kodu

Kodunuzu diğer kod tarafından çağrılan olmaz bir uygulamanın parçası ise, güvenlik basittir ve özel kodlama gerekli olmayabilir. Bununla birlikte, kötü amaçlı kod kodunuzu çağırabilirsiniz unutmayın. Kod erişim güvenliği kaynaklara erişmesini kötü amaçlı kod durdurabilir olsa da, bu tür kodu hala alanları veya hassas bilgiler içerebilir özellikleri değerler okuyabilir.

Ayrıca, kullanıcı girişi Internet'ten veya diğer güvenilir olmayan kaynaklardan kodunuzu kabul ederse, kötü amaçlı girişi hakkında dikkatli olmalıdır.

## <a name="managed-wrapper-to-native-code-implementation"></a>Sarmalayıcı yerel kod uygulamasına yönetilen

Genellikle bu senaryoda, yararlı işlevselliğinin yönetilen kod için kullanılabilir hale getirmek istediğiniz yerel kodda uygulanır. Yönetilen sarmalayıcılar, yazma ya da platform çağırma kullanma veya COM birlikte çalışma için kolaydır. Ancak, bunu yaparsanız, sarmalayıcıları arayanlar başarılı olması için yönetilmeyen kod haklarına sahip olmalıdır. Varsayılan ilke altında bu kod intranetten indirilen veya Internet ile sarmalayıcıları çalışmaz anlamına gelir.

Bu sarmalayıcıları kullanan tüm uygulamalar için yönetilmeyen kod hakları vermek yerine, yalnızca sarmalayıcı kodu bu hakları vermek iyidir. Kaynak temel işlevselliği sunar ve uygulama benzer şekilde güvenli ise, sarmalayıcı yalnızca kendi hakları assert üzerinden çağırmak herhangi bir kod sağlayan gerekir. Kaynaklar dahil edildiğinde güvenlik kodlama sonraki bölümde açıklanan kitaplık kodu çalışması ile aynı olmalıdır. Sarmalayıcı potansiyel olarak bu kaynakları arayanlara gösterme olduğundan, bir yerel kod dikkatli doğrulanması gereklidir ve sarmalayıcının sorumluluğundadır.

## <a name="library-code-that-exposes-protected-resources"></a>Korunan kaynakları gösteren kitaplık kodu

En güçlü ve bu nedenle aşağıdaki yaklaşımı (yanlışlıkla yapıldıysa) potansiyel olarak tehlikeli olabilecek güvenlik kodlamak için: yalnızca .NET sınıfları zorunlu olarak, aksi takdirde, kullanılmayan belirli kaynaklara erişmek başka bir kod için bir arabirimi olarak kitaplığınızın hizmet kullandıkları kaynaklara izinleri. Bir kaynak kullanıma olduğunda, kodunuzu kaynağa uygun izni ilk talep gerekir (diğer bir deyişle, bu bir güvenlik denetimi gerçekleştirmeniz gerekir) ve genellikle gerçek işlemi gerçekleştirmek için kendi haklarını assert.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Durum Verilerinin Güvenliğini Sağlama](securing-state-data.md)|Özel üyelerin korumak açıklar.|
|[Güvenlik ve Kullanıcı Girdisi](security-and-user-input.md)|Bu kullanıcı girişi kabul eden uygulamalar ile ilgili güvenlik konuları açıklanmaktadır.|
|[Güvenlik ve Yarış Durumları](security-and-race-conditions.md)|Yarış durumları kodunuzda önlemek açıklar.|
|[Güvenlik ve Çalışma Sırasında Kod Oluşturma](security-and-on-the-fly-code-generation.md)|Dinamik kodu oluşturmak uygulamalar ile ilgili güvenlik konuları açıklanmaktadır.|
|[Rol Tabanlı Güvenlik](role-based-security.md)|.NET rol tabanlı güvenlik ayrıntılı açıklar ve kodunuzda kullanma yönergeleri sağlar.|
