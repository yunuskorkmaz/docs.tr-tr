---
title: XAMLServices Sınıfı ve Temel XAML Okuma veya Yazma
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: a47436d9f7df099f54d450f6f8176b8cba6d7f5d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622905"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>XAMLServices Sınıfı ve Temel XAML Okuma veya Yazma
<xref:System.Xaml.XamlServices> XAML düğümü akışı özel erişim gerektiren değil XAML senaryoları için kullanılan bir .NET Framework XAML hizmetlerinde tarafından sağlanan sınıfı veya bu düğümünden elde edilen XAML türü sistem bilgileri kullanılabilir. <xref:System.Xaml.XamlServices> API aşağıdaki gibi özetlenen: `Load` veya `Parse` XAML yükleme yolu desteklemek için `Save` kaydetme yolu, bir XAML desteklemek için ve `Transform` bir yükleme yolu birleştiren bir teknik sağlar ve yol kaydetmek için. `Transform` bir XAML şema diğerine geçmek için kullanılabilir. Bu konu, her biri bu API sınıflandırmalar özetler ve belirli bir yöntemi aşırı yüklemeleri arasındaki farklar açıklanmaktadır.  
  
<a name="load"></a>   
## <a name="load"></a>Yükleme  
 Çeşitli aşırı yüklemeleri <xref:System.Xaml.XamlServices.Load%2A> bir yükleme yolu için tam mantığını. Yükleme yolu bazı formunda XAML kullanan ve XAML düğüm akış çıkarır. Bunların çoğu, kodlanmış bir XML metin dosyasını form XAML kullanımda yolları yükleyin. Ancak, genel bir akış da yükleyebilir veya zaten farklı bir yer önceden yüklenmiş bir XAML kaynak yükleyebilir <xref:System.Xaml.XamlReader> uygulaması.  
  
 Çoğu senaryo için basit aşırı <xref:System.Xaml.XamlServices.Load%28System.String%29>. Bu aşırı yüklenmiş bir `fileName` yalnızca yüklemek için XAML içeren bir metin dosyasının adı parametresi. Bu, daha önce eyalet veya yerel bilgisayarda veri serileştirilmiş tam güven uygulamaları gibi uygulama senaryoları için uygundur. Ayrıca, uygulama modelini tanımlama ve uygulama davranışını tanımlayan standart dosyalardan biri yüklemek kullanıcı Arabirimi veya çerçeve tarafından tanımlanmış XAML kullanan diğer özellikleri başlangıç istediğiniz çerçeveleri için kullanışlıdır.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> benzer senaryoları sahiptir. Bu aşırı yükleme yüklenemedi, dosya seçerken, çünkü kullanıcı varsa yararlı olabilir bir <xref:System.IO.Stream> diğer sık kullanılan bir çıktıdır <xref:System.IO> API'leri bir dosya sistemine erişebilir. Veya, XAML kaynakları zaman uyumsuz indirme veya bir akışa sağlayan diğer ağ teknikleri erişiyor. (Yükleme akışı veya kullanıcı tarafından seçilen kaynak güvenlikle ilgili etkileri olabilir. Daha fazla bilgi için [XAML güvenlik konuları](xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> ve <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> okuyucular .NET Framework'ün önceki sürümlerinden biçimlerinin kullanan aşırı yüklemeler. Bu aşırı yüklemeler kullanmak için zaten bir okuyucu örneği oluşturulan ve kullanılan kendi `Create` XAML ilgili biçiminde (metin veya XML) yüklemek için API. Zaten diğer okuyucuların kayıt işaretçileri taşıdığınız veya diğer işlemlerle gerçekleştirilen, bu önemli değildir. Yükleme yolu mantığından <xref:System.Xaml.XamlServices.Load%2A> her zaman aşağı kökünden giriş tüm XAML işler. Bu aşırı yüklemeler için senaryolar şunları içerebilir:  
  
- Varolan bir XML özel metin düzenleyici özelliğini düzenleme basit XAML sağlarsınız yüzeyleri tasarlayın.  
  
- Çekirdek türevleri <xref:System.IO> senaryoları, kullandığınız ayrılmış okuyucular dosyaları ya da akış'ı açmak için. Mantığınızı ilkel denetleme veya XAML yüklemeye çalışmadan önce içeriğini işleme gerçekleştirir.  
  
 Ya da bir dosya veya akışı yükleyebilir veya oluşturduğunuz bir <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, veya <xref:System.Xaml.XamlReader> , kaydırma XAML girişinizi okuyucunun API'lerle yükleyerek.  
  
 Dahili olarak, her biri, önceki aşırı sonuç olduğunu <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>ve geçirilen <xref:System.Xml.XmlReader> yeni oluşturmak için kullanılan <xref:System.Xaml.XamlXmlReader>.  
  
 `Load` Daha Gelişmiş senaryolar sağlar imza <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Bu imza aşağıdaki durumlarda birini kullanabilirsiniz:  
  
- Kendi tanımladığınız bir <xref:System.Xaml.XamlReader>.  
  
- Ayarlarını belirtmek gereken <xref:System.Xaml.XamlReader> varsayılan ayarlardan farklı.  
  
 Varsayılan olmayan ayarların örnekleri ayarladığınızdan aşağıdakilerden herhangi birini: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. İçin varsayılan okuyucu <xref:System.Xaml.XamlServices> olduğu <xref:System.Xaml.XamlXmlReader>. Kendi sağlarsanız <xref:System.Xaml.XamlXmlReader>, ayarlarla, varsayılan olmayan ayarlamak için özellikler şunlardır <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>Ayrıştırma  
 <xref:System.Xaml.XamlServices.Parse%2A> benzer `Load` çünkü bu bir yükleme yolu XAML girişten bir XAML düğümü akışı oluşturan API. Ancak, bu durumda, XAML giriş doğrudan yüklemek için tüm XAML içeren bir dize sağlanır. <xref:System.Xaml.XamlServices.Parse%2A> framework senaryolarından farklı uygulama senaryoları için daha uygun olan basit bir yaklaşımdır. Daha fazla bilgi için bkz. <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A> Aslında Sarmalanan olan <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> içerir çağrısı bir <xref:System.IO.StringReader> dahili olarak.  
  
<a name="save"></a>   
## <a name="save"></a>Kaydet  
 Çeşitli aşırı yüklemeleri <xref:System.Xaml.XamlServices.Save%2A> uygulama kaydetme yolu. Tüm <xref:System.Xaml.XamlServices.Save%2A> girdi ve çıktı olarak bir akış oluşturmak gibi bir nesne grafiğinin tüm getirin yöntemleri dosyası veya <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> örneği.  
  
 Giriş nesnesi, bazı nesne temsili kök nesne olması beklenir. Bu, bir iş nesnesi, bir kullanıcı Arabirimi senaryosunda, çalışma düzenleme yüzeyden tasarım aracı veya senaryoları için uygun olan diğer kök nesne kavramları sayfası için bir nesne ağacının kökü tek kök olabilir.  
  
 XAML ile birlikte yüklenen özgün bir işlemle ilgili pek çok senaryoda kaydettiğiniz nesne ağacının <xref:System.Xaml.XamlServices.Load%2A> veya framework/uygulama modeli tarafından uygulanan diğer API'si ile. Olabilir, durum değişikliklerini, burada, uygulamanızın yakalanan bir kullanıcı çalışma zamanı ayarları değişiklikleri nedeniyle nesne ağacında yakalanan farklar XAML tasarım yüzeyi, vb. uygulamanız olduğu için XAML değiştirildi. İle ya da değişiklik yapmadan kavramı ilk biçimlendirmeden XAML yükleme ve yeniden kaydetmeyi ve iki XAML biçimlendirme formları karşılaştırma, bazen bir gidiş dönüş XAML temsili olarak adlandırılır.  
  
 Kaydetme ve biçimlendirme formunda karmaşık bir nesneyi seri hale getirme ile elde etmeye daha okunabilir XAML yapan ayrıntı ve bilgi kaybı olmadan tam gösterimi arasında bir denge zorluktur. Ayrıca, XAML farklı müşterilerin farklı tanımlara veya bu Bakiye kümesi nasıl beklentileri olabilir. <xref:System.Xaml.XamlServices.Save%2A> API'leri bu Bakiye bir tanımını temsil eder. <xref:System.Xaml.XamlServices.Save%2A> API'leri kullanan mevcut XAML şema içeriği ve CLR tabanlı varsayılan özelliklerini <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, diğer iç XAML ve XAML belirli XAML düğüm akış yapılarını nereye dağıtılacağını belirlemek için sistemi kavramları yazın yeniden biçimlendirme kaydedildiğinde en iyi duruma getirilmiş. Örneğin, <xref:System.Xaml.XamlServices> yolları çözümlemek için CLR tabanlı varsayılan XAML şema içeriği kullanabilir <xref:System.Xaml.XamlType> nesneler için belirleyebilirsiniz bir <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>ve sonra nesnenin XAML içeriği özelliği yazdığınızda özellik öğesi etiketleri atlayabilirsiniz.  
  
<a name="transform"></a>   
## <a name="transform"></a>Dönüştürme  
 <xref:System.Xaml.XamlServices.Transform%2A> dönüştürür veya bir yükleme yolu ve kaydetmeyi bağlayarak XAML dönüştüren tek bir işlem olarak yol. Farklı şema içeriği veya farklı bir yedekleme tür sistemi için kullanılabilir <xref:System.Xaml.XamlReader> ve <xref:System.Xaml.XamlWriter>, olduğu ne elde edilen XAML nasıl dönüştürdüğünü etkiler. Bu geniş dönüştürme işlemleri için iyi çalışır.  
  
 XAML düğümü akışı içindeki her bir düğümün İnceleme üzerinde kullanan işlemleri için genellikle kullanmanızı <xref:System.Xaml.XamlServices.Transform%2A>. Bunun yerine kendi yükleme yolu kayıt yolu işlemi tanımlamanız ve kendi mantığınızı interject gerekir. Yolları her birinde bir XAML okuyucu/XAML yazıcı çifti kendi düğüm döngü etrafında kullanın. Örneğin, ilk XAML kullanarak yük <xref:System.Xaml.XamlXmlReader> ve düğümleri art arda gelen adımla <xref:System.Xaml.XamlXmlReader.Read%2A> çağırır. XAML düğüm akış düzeyinde, işletim artık bir dönüştürme uygulamak için tek tek düğümleri (türleri, üyeler, diğer düğümler) ayarlayabilir veya düğüm olarak bırakın-olduğu. Düğüm ve sonraki sürümlerde ilgili gönderdiğiniz sonra `Write` API'si, bir <xref:System.Xaml.XamlObjectWriter> ve nesne yazma. Daha fazla bilgi için [anlama XAML düğüm Stream yapılarını ve kavramlarını](understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [XAML Hizmetleri](index.md)
