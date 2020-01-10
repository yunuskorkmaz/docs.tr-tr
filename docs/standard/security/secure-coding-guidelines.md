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
ms.openlocfilehash: 51f835803cc545e2a9982c1c8a90d0c998c2bcb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705918"
---
# <a name="secure-coding-guidelines"></a>Güvenli kodlama yönergeleri

Kanıt tabanlı güvenlik ve kod erişim güvenliği, güvenliği uygulamak için çok güçlü ve açık mekanizmalar sağlar. Çoğu uygulama kodu yalnızca .NET tarafından uygulanan altyapıyı kullanabilir. Bazı durumlarda, güvenlik sistemini genişleterek veya yeni geçici yöntemler kullanılarak oluşturulan uygulamaya özgü ek güvenlik gerekir.

Kodunuzda .NET tarafından zorlanan izinleri ve diğer uygulamayı kullanarak, kötü amaçlı kodun, istemediğiniz bilgilere erişmesini veya başka istenmeyen eylemler gerçekleştirmesini istemediğiniz bilgilere erişmesini önlemeye yönelik engelleri almalısınız. Ayrıca, güvenilen kod kullanarak beklenen tüm senaryolarda güvenlik ve kullanılabilirlik arasında bir denge oluşturmanız gerekir.

Bu genel bakışta kodun güvenlik sistemiyle çalışmak için tasarlanma yöntemi açıklanmaktadır.

## <a name="securing-resource-access"></a>Kaynak erişiminin güvenliğini sağlama

Kodunuzu tasarlarken ve yazarken, özellikle de bilinmeyen kaynak kodu kullanırken veya çağırılırken, kodun kaynaklarla olan erişimini korumanız ve sınırlamanız gerekir. Bu nedenle, kodunuzun güvende olduğundan emin olmak için aşağıdaki teknikleri aklınızda bulundurun:

- Kod erişim güvenliği (CAS) kullanmayın.

- Kısmi güvenilir kod kullanmayın.

- [Allowpartiallytrustedcaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) özniteliğini (aptca) kullanmayın.

- .NET uzaktan Iletişim kullanmayın.

- Dağıtılmış bileşen nesne modeli (DCOM) kullanmayın.

- İkili formatlayıcıları kullanmayın.

Kod erişimi güvenliği ve güvenlik açısından saydam kod, kısmen güvenilen kod içeren bir güvenlik sınırı olarak desteklenmez. Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez. Alternatif güvenlik ölçüleri şunlardır:

- Sanallaştırma

- AppContainers

- İşletim sistemi (OS) kullanıcıları ve izinleri

- Hyper-V kapsayıcıları

## <a name="security-neutral-code"></a>Güvenlikle bağımsız kod

Güvenlik için bağımsız kod, güvenlik sistemiyle hiçbir şey yapmaz. Aldığı izinlerle çalışır. Korunan işlemlerle ilişkili güvenlik özel durumlarını (örneğin, dosya kullanımı, ağ ve benzeri) yakalayamayan uygulamalar işlenmeyen bir özel durumla sonuçlansa da, güvenlikle bağımsız kod yine de .NET 'teki güvenlik teknolojilerinden faydalanır .

Güvenlikle bağımsız bir kitaplıkta anlamanız gereken özel özellikler vardır. Kitaplığınızın dosyaları kullanan veya yönetilmeyen kodu çağıran API öğeleri sağladığını varsayalım. Kodunuzun karşılık gelen izni yoksa, açıklanan şekilde çalışmaz. Ancak, kod izne sahip olsa bile, çağıran herhangi bir uygulama kodunun çalışması için aynı izne sahip olması gerekir. Çağıran kodun doğru izni yoksa, kod erişimi güvenlik yığını yürüme sonucu olarak bir <xref:System.Security.SecurityException> görüntülenir.

## <a name="application-code-that-isnt-a-reusable-component"></a>Yeniden kullanılabilir bir bileşen olmayan uygulama kodu

Kodunuz, başka kod tarafından çağrılmayan bir uygulamanın parçasıysa, güvenlik basittir ve özel kodlama gerekli olmayabilir. Ancak, kötü amaçlı kodun kodunuzun çağıraolabileceğini unutmayın. Kod erişimi güvenliği kötü amaçlı kodun kaynaklara erişmesini durdurmasına karşın, bu kod, gizli bilgiler içerebilen alanlarınızın veya özelliklerinin değerlerini yine de okuyabilir.

Ayrıca, kodunuz Internet veya diğer güvenilir olmayan kaynaklardan Kullanıcı girişini kabul ediyorsa kötü amaçlı giriş konusunda dikkatli olmanız gerekir.

## <a name="managed-wrapper-to-native-code-implementation"></a>Yerel kod uygulamasına yönetilen sarmalayıcı

Genellikle bu senaryoda, bazı yararlı işlevler, yönetilen kod için kullanılabilir hale getirmek istediğiniz yerel kodda uygulanır. Yönetilen sarmalayıcılardan, platform çağırma veya COM birlikte çalışabilirliği kullanılarak kolayca yazılabilir. Ancak bunu yaparsanız, sarmalayıcılarınızın başarılı olması için yönetilmeyen kod haklarına sahip olması gerekir. Varsayılan ilke altında bu, bir intranet veya Internet 'ten indirilen kodun sarmalayıcılarla birlikte çalışacağı anlamına gelir.

Bu sarmalayıcıları kullanan tüm uygulamalara yönetilmeyen kod hakları vermek yerine, bu hakları yalnızca sarmalayıcı koduna vermek daha iyidir. Temeldeki işlevsellik hiçbir kaynak açığa çıkardığı ve uygulamanın aynı şekilde güvende olması halinde, sarmalayıcının yalnızca kendi haklarını sağlaması gerekir, bu da herhangi bir kodun bunun üzerinde çağrı yapmasına olanak sağlar. Kaynaklar dahil edildiğinde, güvenlik kodlaması, sonraki bölümde açıklanan kitaplık kodu durumuyla aynı olmalıdır. Sarmalayıcı, bu kaynaklara çağıranları ortaya çıkardığından, yerel kodun güvenliğine dikkat etmeniz gerekir ve sarmalayıcı sorumluluğunda olur.

## <a name="library-code-that-exposes-protected-resources"></a>Korumalı kaynakları açığa çıkaran kitaplık kodu

Aşağıdaki yaklaşım, güvenlik kodlaması için en güçlü ve potansiyel olarak tehlikeli (yanlış yapılmasa) olabilir: kitaplığınız, .NET sınıflarının zorunlu olduğu gibi, başka bir şekilde kullanılamayan belirli kaynaklara erişmek için bir arabirim görevi görür kullandıkları kaynaklar için izinler. Bir kaynağı kullanıma sunduğunuzdan, kodunuzun öncelikle kaynağa uygun olan izni talep etmelidir (yani, bir güvenlik denetimi gerçekleştirmesi gerekir) ve tipik olarak gerçek işlemi gerçekleştirmek için haklarını onaylayın.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Durum Verilerinin Güvenliğini Sağlama](securing-state-data.md)|Özel üyelerin nasıl korunacağını açıklar.|
|[Güvenlik ve Kullanıcı Girdisi](security-and-user-input.md)|Kullanıcı girişini kabul eden uygulamalar için güvenlik konularını açıklar.|
|[Güvenlik ve Yarış Durumları](security-and-race-conditions.md)|Kodunuzda yarış durumlarının nasıl önleneceğini açıklar.|
|[Güvenlik ve Çalışma Sırasında Kod Oluşturma](security-and-on-the-fly-code-generation.md)|Dinamik kod üreten uygulamalarla ilgili güvenlik konularını açıklar.|
|[Rol Tabanlı Güvenlik](role-based-security.md)|.NET rol tabanlı güvenliği ayrıntılı olarak açıklar ve kodunuzda kullanmak için yönergeler sağlar.|
