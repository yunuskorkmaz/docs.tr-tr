---
title: "XAMLServices Sınıfı ve Temel XAML Okuma veya Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30d94534f0da0e3946d036fd8e0db59971615c0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>XAMLServices Sınıfı ve Temel XAML Okuma veya Yazma
<xref:System.Xaml.XamlServices>XAML düğümü akışı belirli erişim gerektiriyor mu XAML senaryosu için kullanılan bir .NET Framework XAML Hizmetleri tarafından sağlanan sınıfı veya bu düğümlerden alınan XAML tür sistem bilgileri değil. <xref:System.Xaml.XamlServices>API aşağıdaki gibi özetlenen: `Load` veya `Parse` XAML yükleme yolu desteklemek için `Save` kaydetme yolu, bir XAML desteklemek için ve `Transform` bir yükleme yolu katıldığı bir teknik sağlamak ve yolunu kaydedin. `Transform`başka bir XAML şema değiştirmek için kullanılabilir. Bu konu, her biri bu API sınıflandırmalarını özetler ve belirli yöntemi aşırı yüklemeleri arasındaki farklar açıklanmaktadır.  
  
<a name="load"></a>   
## <a name="load"></a>Yükleme  
 Çeşitli aşırı <xref:System.Xaml.XamlServices.Load%2A> bir yükleme yolu için tam mantığı uygular. Yükleme yolu XAML bazı formunda kullanır ve XAML düğümü akışı çıkarır. Bunların çoğu kodlanmış bir XML metin dosyası form XAML kullanımda yolları yükleyin. Ancak, genel bir akış da yükleyebilir veya zaten farklı bir yer önceden yüklenmiş bir XAML kaynağı yükleyebilir <xref:System.Xaml.XamlReader> uygulaması.  
  
 Çoğu senaryo için basit aşırı yüklemesi, <xref:System.Xaml.XamlServices.Load%28System.String%29>. Bu aşırı yüklemesi olan bir `fileName` yalnızca yüklemek için XAML içeren bir metin dosyası adı parametresi. Bu, daha önce durumu veya yerel bilgisayarda verileri seri hale getirilmiş tam güven uygulamaları gibi uygulama senaryolar için uygundur. Bu da burada uygulama modeli tanımlama ve uygulama davranışını tanımlayan standart dosyalarından birini yük UI ya da XAML kullanan diğer framework tanımlı yetenekleri başlangıç istediğiniz çerçeveyi yararlı olur.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29>benzer senaryolar vardır. Bu aşırı yüklemek için dosyaları seçerken, çünkü kullanıcı varsa yararlı olabilecek bir <xref:System.IO.Stream> sık çıktısı, diğer <xref:System.IO> bir dosya sistemine erişebilir API'leri. Veya, XAML kaynakları zaman uyumsuz yüklemeleri veya aynı zamanda bir akışı sağlamak diğer ağ teknikleri erişiyor. (Yükleme akışı veya kullanıcı tarafından seçilen kaynak güvenlik etkileri olabilir. Daha fazla bilgi için bkz: [XAML güvenlik konuları](../../../docs/framework/xaml-services/xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29>ve <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> .NET Framework'ün önceki sürümlerden biçimlerinin okuyucular Bel aşırı şunlardır. Bu aşırı kullanmak için zaten bir okuyucu örneği oluşturulan ve kullanılan kendi `Create` XAML ilgili biçiminde (metin veya XML) yüklemek için API. Zaten başka bir okuyucu kayıt işaretçileri taşınmış veya diğer işlemleriyle gerçekleştirilen varsa, bu önemli değildir. Yükleme yolu mantığından <xref:System.Xaml.XamlServices.Load%2A> her zaman aşağı kökünden giriş tüm XAML işler. Bu aşırı yüklemeleri için senaryolar aşağıdakileri içerebilir:  
  
-   Varolan bir XML özel metin düzenleyici özelliğinden düzenleme basit XAML Burada sağladığınız yüzeyleri tasarlayın.  
  
-   Çekirdek çeşitlemelerini <xref:System.IO> kullandığınız ayrılmış okuyucular dosyalarını veya akışları senaryoları. Mantığınızı ilkel denetleme veya XAML yüklemeye çalışmadan önce içeriğini işleme gerçekleştirir.  
  
 Bir dosya veya akış ya da yükleyebilir veya yükleyebilirsiniz bir <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, veya <xref:System.Xaml.XamlReader> , sarmalama XAML girişinizi okuyucunun API'leri ile yükleyerek.  
  
 Dahili olarak, her önceki aşırı sonuçta olan <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>ve geçirilen <xref:System.Xml.XmlReader> yeni oluşturmak için kullanılan <xref:System.Xaml.XamlXmlReader>.  
  
 `Load` Daha Gelişmiş senaryolar sağlar imza <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Bu imza aşağıdaki durumlarda birini kullanabilirsiniz:  
  
-   Kendi tanımladığınız bir <xref:System.Xaml.XamlReader>.  
  
-   Ayarlarını belirtmek gereken <xref:System.Xaml.XamlReader> varsayılan ayarlardan farklı.  
  
 Varsayılan olmayan ayarların örneklerini ayarladığınızdan aşağıdakilerden herhangi birini: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. İçin varsayılan okuyucu <xref:System.Xaml.XamlServices> olan <xref:System.Xaml.XamlXmlReader>. Kendi sağlarsanız, <xref:System.Xaml.XamlXmlReader>, ayarları, varsayılan olmayan ayarlamak için özellikleri şunlardır <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>Ayrıştırma  
 <xref:System.Xaml.XamlServices.Parse%2A>benzer `Load` bir yükleme yolu bir XAML düğümü akışı XAML girişten oluşturur API olduğundan. Ancak, bu durumda, XAML giriş doğrudan yük XAML içeren bir dize sağlanır. <xref:System.Xaml.XamlServices.Parse%2A>framework senaryoları uygulama senaryoları için daha uygun olan basit bir yaklaşımdır. Daha fazla bilgi için bkz. <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A>Aslında Sarmalanan olan <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> içerir çağrısı bir <xref:System.IO.StringReader> dahili olarak.  
  
<a name="save"></a>   
## <a name="save"></a>Kaydet  
 Çeşitli aşırı <xref:System.Xaml.XamlServices.Save%2A> kaydetme uygulama yolu. Tüm <xref:System.Xaml.XamlServices.Save%2A> tüm ele olarak giriş ve çıkış bir akış olarak üreten bir nesne grafiğinin yöntemleri dosyası veya <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> örneği.  
  
 Giriş nesnesi, bazı nesne temsili kök nesne olması beklenir. Bu, tek bir iş nesnesi, bir nesne ağacına UI senaryosunda, çalışma düzenleme yüzeyden bir tasarım aracı veya senaryolar için uygun olan diğer kök nesnesi kavramları sayfası için kök kökündeki olabilir.  
  
 Birçok senaryoda kaydettiğiniz nesne ağacına XAML ile birlikte yüklenen bir özgün işlemi ilgili <xref:System.Xaml.XamlServices.Load%2A> veya framework/uygulama modeli tarafından uygulanan diğer API ile. Olabilir durumu değişiklikler, burada, uygulamanızın yakalanan bir kullanıcıdan çalışma zamanı ayarları nedeniyle olan nesne ağacında yakalanan farklar uygulamanızı XAML tasarım yüzeyi, vb. olduğundan XAML değiştirildi. İle ya da değişiklik yapmadan ilk XAML biçimlendirmeden yükleme ve yeniden kaydetmeyi ve iki XAML işaretleme forms karşılaştırma kavramı bazen XAML gidiş dönüş gösterimi adlandırılır.  
  
 Kaydetme ve biçimlendirme formunda karmaşık bir nesne seri hale getirme ile XAML daha okunabilir hale getirir ayrıntı karşı bilgi kaybı olmadan tam gösterimi arasında bir denge elde etmedeki iştir. Ayrıca, çeşitli müşteriler için XAML farklı tanımlarını veya bu denge nasıl ayarlamak için beklentilerini olabilir. <xref:System.Xaml.XamlServices.Save%2A> API'leri bu denge bir tanımını temsil eder. <xref:System.Xaml.XamlServices.Save%2A> API'lerini kullanan kullanılabilir XAML şema içeriği ve CLR tabanlı varsayılan özelliklerini <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, diğer iç XAML ve XAML belirli XAML düğüm akış yapılarını burada olabilir belirlemek için sistem kavramları yazın geri biçimlendirme kaydedildiğinde en iyi duruma getirilmiş. Örneğin, <xref:System.Xaml.XamlServices> yolları çözümlemek için CLR göre varsayılan XAML şema içeriği kullanabilir <xref:System.Xaml.XamlType> nesneleri için belirleyebilirsiniz bir <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>ve nesnenin XAML içeriği özelliği yazdığınızda özellik öğesi etiketleri sonra atlayabilirsiniz.  
  
<a name="transform"></a>   
## <a name="transform"></a>Dönüştürme  
 <xref:System.Xaml.XamlServices.Transform%2A>dönüştürür veya bir yükleme yolu ve bir Kaydet bağlanmasıyla XAML dönüştüren yolu tek bir işlem olarak. Farklı şema bağlamı veya farklı yedekleme tür sistemi için kullanılabilir <xref:System.Xaml.XamlReader> ve <xref:System.Xaml.XamlWriter>, olduğu ne elde edilen XAML nasıl dönüştürülür etkiler. Bu da geniş dönüştürme işlemleri için çalışır.  
  
 XAML düğümü akışı içindeki her bir düğümün inceleniyor kullanan işlemleri için genellikle kullanmaz <xref:System.Xaml.XamlServices.Transform%2A>. Bunun yerine, kendi yükleme yolu kaydetme yolu işlemi tanımlamanız ve kendi mantığınızı interject gerekir. Yollar her birinde bir XAML okuyucu/XAML yazan çifti düğümü Döngü geçici kullanın. Örneğin, ilk XAML kullanılarak yük <xref:System.Xaml.XamlXmlReader> ve art arda düğümlerle adımla <xref:System.Xaml.XamlXmlReader.Read%2A> çağrıları. XAML düğüm akış düzeyinde işletim şimdi bir dönüşüm uygulamak tek düğümler (türleri, üyeler, diğer düğümler) ayarlayabilir veya düğüm olarak bırakın-değil. Düğüm ve sonraki sürümleri ilgili gönderdiğiniz sonra `Write` API'si bir <xref:System.Xaml.XamlObjectWriter> ve nesne yazma. Daha fazla bilgi için bkz: [anlama XAML düğüm akış yapılarını ve kavramlarını](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xaml.XamlObjectWriter>  
 <xref:System.Xaml.XamlServices>  
 [XAML Hizmetleri](../../../docs/framework/xaml-services/index.md)
