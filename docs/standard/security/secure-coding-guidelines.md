---
title: .NET için güvenli kodlama yönergeleri
description: Birlikte çalışmak için tasarım kodu. Kötü amaçlı kodun verilere erişmesini veya diğer eylemleri gerçekleştirmesini önlemeye yardımcı olmak için NET uygulama izinleri ve diğer zorlama.
ms.date: 07/15/2020
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
ms.openlocfilehash: a05e0cec2814be88ac835d05601d5cf5f66383c3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555962"
---
# <a name="secure-coding-guidelines"></a>Güvenli kodlama yönergeleri

Çoğu uygulama kodu yalnızca .NET tarafından uygulanan altyapıyı kullanabilir. Bazı durumlarda, güvenlik sistemini genişleterek veya yeni geçici yöntemler kullanılarak oluşturulan uygulamaya özgü ek güvenlik gerekir.

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

Güvenlik için bağımsız kod, güvenlik sistemiyle hiçbir şey yapmaz. Aldığı izinlerle çalışır. Korunan işlemlerle ilişkili güvenlik özel durumlarını (örneğin, dosya ve ağ kullanımı gibi) yakalayamayan uygulamalar işlenmeyen bir özel durumla sonuçlansa da, güvenlikle bağımsız kod yine de .NET 'teki güvenlik teknolojilerinden faydalanır.

Güvenlikle bağımsız bir kitaplıkta anlamanız gereken özel özellikler vardır. Kitaplığınızın dosyaları kullanan veya yönetilmeyen kodu çağıran API öğeleri sağladığını varsayalım. Kodunuzun karşılık gelen izni yoksa, açıklanan şekilde çalışmaz. Ancak, kod izne sahip olsa bile, çağıran herhangi bir uygulama kodunun çalışması için aynı izne sahip olması gerekir. Çağıran kodun doğru izni yoksa, <xref:System.Security.SecurityException> kod erişimi güvenlik yığını ilermasının sonucu olarak bir görünür.

## <a name="application-code-that-isnt-a-reusable-component"></a>Yeniden kullanılabilir bir bileşen olmayan uygulama kodu

Kodunuz, başka kod tarafından çağrılmayan bir uygulamanın parçasıysa, güvenlik basittir ve özel kodlama gerekli olmayabilir. Ancak, kötü amaçlı kodun kodunuzun çağıraolabileceğini unutmayın. Kod erişimi güvenliği kötü amaçlı kodun kaynaklara erişmesini durdurmasına karşın, bu kod, gizli bilgiler içerebilen alanlarınızın veya özelliklerinin değerlerini yine de okuyabilir.

Ayrıca, kodunuz Internet veya diğer güvenilir olmayan kaynaklardan Kullanıcı girişini kabul ediyorsa kötü amaçlı giriş konusunda dikkatli olmanız gerekir.

## <a name="managed-wrapper-to-native-code-implementation"></a>Yerel kod uygulamasına yönetilen sarmalayıcı

Genellikle bu senaryoda, bazı yararlı işlevler, yönetilen kod için kullanılabilir hale getirmek istediğiniz yerel kodda uygulanır. Yönetilen sarmalayıcılardan, platform çağırma veya COM birlikte çalışabilirliği kullanılarak kolayca yazılabilir. Ancak bunu yaparsanız, sarmalayıcılarınızın başarılı olması için yönetilmeyen kod haklarına sahip olması gerekir. Varsayılan ilke altında bu, bir intranet veya Internet 'ten indirilen kodun sarmalayıcılarla birlikte çalışacağı anlamına gelir.

Bu sarmalayıcıları kullanan tüm uygulamalara yönetilmeyen kod hakları vermek yerine, bu hakları yalnızca sarmalayıcı koduna vermek daha iyidir. Temeldeki işlevsellik hiçbir kaynak açığa çıkardığı ve uygulamanın aynı şekilde güvende olması halinde, sarmalayıcının yalnızca kendi haklarını sağlaması gerekir, bu da herhangi bir kodun bunun üzerinde çağrı yapmasına olanak sağlar. Kaynaklar dahil edildiğinde, güvenlik kodlaması, sonraki bölümde açıklanan kitaplık kodu durumuyla aynı olmalıdır. Sarmalayıcı, bu kaynaklara çağıranları ortaya çıkardığından, yerel kodun güvenliğine dikkat etmeniz gerekir ve sarmalayıcı sorumluluğunda olur.

## <a name="library-code-that-exposes-protected-resources"></a>Korumalı kaynakları açığa çıkaran kitaplık kodu

Aşağıdaki yaklaşım, güvenlik kodlaması için en güçlü ve potansiyel olarak tehlikeli (yanlış yapılmasa) olabilir: kitaplığınız, .NET sınıflarının kullandıkları kaynaklar için izinleri zorladığından, diğer kodun başka bir şekilde kullanılamayan belirli kaynaklara erişmesi için bir arabirim görevi görür. Bir kaynağı kullanıma sunduğunuzdan, kodunuzun öncelikle kaynağa uygun olan izni talep etmelidir (yani, bir güvenlik denetimi gerçekleştirmesi gerekir) ve tipik olarak gerçek işlemi gerçekleştirmek için haklarını onaylayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Durum Verilerinin Güvenliğini Sağlama](securing-state-data.md)
- [Güvenlik ve Kullanıcı Girdisi](security-and-user-input.md)
- [Güvenlik ve Yarış Durumları](security-and-race-conditions.md)
- [Güvenlik ve Çalışma Sırasında Kod Oluşturma](security-and-on-the-fly-code-generation.md)
- [Rol Tabanlı Güvenlik](role-based-security.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
