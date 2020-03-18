---
title: .NET için güvenli kodlama yönergeleri
description: Çalışmak için tasarım kodu. Kötü amaçlı kodların verilere erişmesini veya diğer eylemleri gerçekleştirmesini önlemeye yardımcı olmak için NET tarafından uygulanan izinler ve diğer zorlamalar.
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
ms.openlocfilehash: 05f7e039ecdc0cd33baa015872924fb9e1f078aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187724"
---
# <a name="secure-coding-guidelines"></a>Güvenli kodlama yönergeleri

Kanıta dayalı güvenlik ve kod erişim güvenliği, güvenliği uygulamak için çok güçlü ve açık mekanizmalar sağlar. Çoğu uygulama kodu sadece .NET tarafından uygulanan altyapık kullanabilirsiniz. Bazı durumlarda, güvenlik sistemini genişleterek veya yeni geçici yöntemler kullanılarak oluşturulmuş ek uygulamaya özgü güvenlik gerekir.

Kodunuzda .NET zorunlu izinleri ve diğer zorlamaları kullanarak, kötü amaçlı kodun sahip olmasını istemediğiniz bilgilere erişmesini veya diğer istenmeyen eylemleri gerçekleştirmesini engellemek için engeller getirmelisiniz. Ayrıca, güvenilen kodu kullanarak beklenen tüm senaryolarda güvenlik ve kullanılabilirlik arasında bir denge kurmanız gerekir.

Bu genel bakış, kodun güvenlik sistemiyle çalışmak üzere tasarlanabileceği farklı yolları açıklar.

## <a name="securing-resource-access"></a>Kaynak erişimini sağlama

Kodunuzu tasarlarken ve yazarken, özellikle kaynağı bilinmeyen kodu kullanırken veya çağırırken, bu kodun kaynaklara erişimini korumanız ve sınırlamanız gerekir. Bu nedenle, kodunuzu güvenli olduğundan emin olmak için aşağıdaki teknikleri aklınızda bulundurun:

- Kod Erişim Güvenliği (CAS) kullanmayın.

- Kısmi güvenilir kod kullanmayın.

- [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) özniteliğini (APTCA) kullanmayın.

- .NET Remoting kullanmayın.

- Dağıtılmış Bileşen Nesne Modeli (DCOM) kullanmayın.

- İkili formatters kullanmayın.

Kod Erişim Güvenliği ve Güvenlik Saydam Kodu, kısmen güvenilen koda sahip bir güvenlik sınırı olarak desteklenmez. Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez. Alternatif güvenlik önlemleri şunlardır:

- Sanallaştırma

- AppContainers

- İşletim sistemi (OS) kullanıcıları ve izinleri

- Hyper-V konteynerler

## <a name="security-neutral-code"></a>Güvenlik-nötr kodu

Güvenlikten bağımsız kod, güvenlik sisteminde açık bir şey yapmaz. Aldığı izinlerle çalışır. Korumalı işlemlerle ilişkili güvenlik özel durumlarını yakalayamayan uygulamalar (dosya kullanma, ağ vb. gibi) işlenmemiş bir özel durumla sonuçlanabilir, ancak güvenlikten bağımsız kod yine de .NET'teki güvenlik teknolojilerinden yararlanır .

Güvenlik-nötr kitaplık anlamanız gereken özel özelliklere sahiptir. Kitaplığınızın dosyaları kullanan veya yönetilmeyen kod çağrısında kullanılan API öğeleri sağladığını varsayalım. Kodunuz ilgili izine sahip değilse, açıklandığı gibi çalışmaz. Ancak, kod izinolsa bile, kodu çağıran herhangi bir uygulama kodunun çalışabilmesi için aynı izne sahip olması gerekir. Arama kodu doğru izine sahip değilse, <xref:System.Security.SecurityException> kod erişim güvenlik yığını yürüyüşünün bir sonucu olarak bir görüntü görüntülenir.

## <a name="application-code-that-isnt-a-reusable-component"></a>Yeniden kullanılabilir bir bileşen olmayan uygulama kodu

Kodunuz başka kod tarafından çağrılmayacak bir uygulamanın parçasıysa, güvenlik basittir ve özel kodlama gerekli olmayabilir. Ancak, kötü amaçlı kodun kodunuzu çağırabileceğini unutmayın. Kod erişim güvenliği kötü amaçlı kodun kaynaklara erişmesini durdurabilir, ancak bu kod alanlarınızın değerlerini veya hassas bilgiler içerebilecek özellikleri okumaya devam edebilir.

Ayrıca, kodunuz Internet'ten veya diğer güvenilir olmayan kaynaklardan kullanıcı girişi kabul ederse, kötü amaçlı giriş konusunda dikkatli olmalısınız.

## <a name="managed-wrapper-to-native-code-implementation"></a>Yerel kod uygulamasına yönetilen sarıcı

Genellikle bu senaryoda, yönetilen kod için kullanılabilir hale getirmek istediğiniz yerel kodda bazı yararlı işlevler uygulanır. Yönetilen sarmalayıcıları platform çağırmak veya COM interop kullanarak yazmak kolaydır. Ancak, bunu yaparsanız, sarmalayıcılarınızın başarılı olması için yönetilmeyen kod haklarına sahip olması gerekir. Varsayılan ilke altında, bu, intranet veya Internet'ten indirilen kodun sarmalayıcılarla çalışmayamayacağı anlamına gelir.

Bu sarıcıları kullanan tüm uygulamalara yönetilmeyen kod hakları vermek yerine, bu hakları yalnızca sarıcı koduna vermek daha iyidir. Altta yatan işlevsellik hiçbir kaynak ortaya çıkarır ve uygulama aynı şekilde güvenli ise, sarıcı yalnızca herhangi bir kodun üzerinden aramasını sağlayan haklarını kanıtlaması gerekir. Kaynaklar söz konusu olduğunda, güvenlik kodlaması sonraki bölümde açıklanan kitaplık kodu örneğiyle aynı olmalıdır. Sarmalayıcı potansiyel olarak arayanları bu kaynaklara maruz bıraktığından, yerel kodun güvenliğinin dikkatli bir şekilde doğrulanması gereklidir ve paketleyicinin sorumluluğundadır.

## <a name="library-code-that-exposes-protected-resources"></a>Korumalı kaynakları ortaya çıkaran kitaplık kodu

Aşağıdaki yaklaşım, güvenlik kodlaması için en güçlü ve dolayısıyla tehlikeli (yanlış yapılırsa) olabilir: kitaplığınız, .NET sınıfları gibi başka türlü kullanılamayan belirli kaynaklara erişmek için diğer kodlar için bir arabirim görevi görür kullandıkları kaynaklar için izinler. Bir kaynağı nereye maruz bırakırsanız ortaya çıkarırsanız gösterin, kodunuz önce kaynağa uygun izni talep etmeli (diğer bir süre önce bir güvenlik denetimi gerçekleştirmesi gerekir) ve ardından genellikle gerçek işlemi gerçekleştirmek için haklarını ileri sürmelidir.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Durum Verilerinin Güvenliğini Sağlama](securing-state-data.md)|Özel üyelerin nasıl korunacaklarını açıklar.|
|[Güvenlik ve Kullanıcı Girdisi](security-and-user-input.md)|Kullanıcı girişi kabul eden uygulamaların güvenlik kaygılarını açıklar.|
|[Güvenlik ve Yarış Durumları](security-and-race-conditions.md)|Kodunuzda yarış koşullarından nasıl kaçınılabildiğini açıklar.|
|[Güvenlik ve Çalışma Sırasında Kod Oluşturma](security-and-on-the-fly-code-generation.md)|Dinamik kod oluşturan uygulamaların güvenlik kaygılarını açıklar.|
|[Rol Tabanlı Güvenlik](role-based-security.md)|.NET rol tabanlı güvenliği ayrıntılı olarak açıklar ve kodunızda kullanmak için yönergeler sağlar.|
