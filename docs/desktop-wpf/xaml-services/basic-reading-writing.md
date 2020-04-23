---
title: XAMLServices Sınıfı ve Temel XAML Okuma veya Yazma
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 264a8c4abcf9a7efceb7c7accd786495d35476e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071880"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>XAMLServices sınıf ve temel XAML okuma veya yazma

<xref:System.Xaml.XamlServices>.NET tarafından sağlanan ve XAML düğüm akışına veya bu düğümlerden elde edilen XAML türü sistem bilgilerine özel erişim gerektirmeyen XAML senaryolarını ele almak için kullanılabilen bir sınıftır. <xref:System.Xaml.XamlServices>API aşağıdaki gibi `Load` özetlenebilir: `Parse` veya xaml yük `Save` yolunu desteklemek, bir XAML `Transform` kaydetme yolunu desteklemek ve bir yük yolunu birleştiren ve yolu kaydeden bir teknik sağlamak için. `Transform`bir XAML şemasından diğerine geçiş için kullanılabilir. Bu konu, bu API sınıflandırmalarının her birini özetler ve belirli yöntem aşırı yüklemeleri arasındaki farkları açıklar.

## <a name="load"></a>Yükleme

Çeşitli aşırı <xref:System.Xaml.XamlServices.Load%2A> yükler, bir yük yolu için tam mantığı uygular. Yük yolu bazı biçimlerde XAML kullanır ve bir XAML düğüm akışı çıkar. Bu yükleme yollarının çoğu kodlanmış bir XML metin dosyası formunda XAML kullanır. Ancak, genel bir akış da yükleyebilir veya zaten farklı <xref:System.Xaml.XamlReader> bir uygulamada bulunan önceden yüklenmiş bir XAML kaynağı yükleyebilirsiniz.

Çoğu senaryo için en basit <xref:System.Xaml.XamlServices.Load%28System.String%29>aşırı yük . Bu aşırı yükleme, yalnızca yüklenmesi gereken XAML'yi içeren bir metin dosyasının adı olan bir `fileName` parametreye sahiptir. Bu, daha önce durumu veya verileri yerel bilgisayara serileştirmiş tam güven uygulamaları gibi uygulama senaryoları için uygundur. Bu, uygulama modelini tanımladığınız ve uygulama davranışını tanımlayan, Kullanıcı Arasını başlatan veya XAML kullanan diğer çerçeve tanımlı özelliklerden birini yüklemek istediğiniz çerçeveler için de yararlıdır.

<xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29>benzer senaryolara sahiptir. Bir dosya sistemine erişebilen diğer <xref:System.IO.Stream> <xref:System.IO> API'lerin sık sık çıktısı olduğundan, kullanıcının yüklemek için dosyaları seçmesi gerekiyorsa, bu aşırı yükleme yararlı olabilir. Veya xaml kaynaklarına eşzamanlı indirmeler veya akış sağlayan diğer ağ teknikleri aracılığıyla erişiyor olabilirsiniz. (Bir akıştan veya kullanıcı tarafından seçilen bir kaynaktan yüklemenin güvenlik etkileri olabilir. Daha fazla bilgi için Bkz. [XAML Güvenlik Hususları](security-considerations.md).)

<xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29>ve <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> .NET'in önceki sürümlerindeki biçimlerin okuyucularına dayanan aşırı yüklerdir. Bu aşırı yüklemeleri kullanmak için, zaten bir okuyucu `Create` örneği oluşturmuş ve XAML'yi ilgili forma (metin veya XML) yüklemek için API'sini kullanmış olmalısınız. Kayıt işaretçilerini zaten diğer okuyuculara taşıdıysanız veya onlarla birlikte başka işlemler gerçekleştirdiyseniz, bu önemli değildir. Yük yolu mantığı <xref:System.Xaml.XamlServices.Load%2A> her zaman kökten aşağı tüm XAML girişi işler. Aşağıdaki senaryolar, bu aşırı yüklerin kullanımını garanti edebilir:

- Varolan XML'e özgü metin düzenleyicisinden basit XAML düzenleme özelliği sağladığınız tasarım yüzeyleri.

- Dosyaları veya akışları <xref:System.IO> açmak için özel okuyucuları kullandığınız temel senaryoların türevleri. Mantığınız, XAML olarak yüklemeye başlamadan önce içeriği temel olarak denetlemeyi veya işlemeyi gerçekleştirir.

Bir dosyayı veya akışı yükleyebilirsiniz veya <xref:System.Xml.XmlReader>okuyucunun API'leri ile yükleyerek XAML girişinizi sarar bir , <xref:System.IO.TextReader>yükleyebilirsiniz. <xref:System.Xaml.XamlReader>

Dahili olarak, önceki aşırı yüklerin <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>her biri <xref:System.Xml.XmlReader> sonuçta , ve <xref:System.Xaml.XamlXmlReader>geçen yeni bir oluşturmak için kullanılır .

Daha `Load` gelişmiş senaryolar sağlayan imza. <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29> Bu imzayı aşağıdaki durumlardan biri için kullanabilirsiniz:

- Kendi uygulamanızı <xref:System.Xaml.XamlReader>tanımladınız.

- Varsayılan ayarlardan farklı <xref:System.Xaml.XamlReader> ayarlar belirtmeniz gerekir.

Varsayılan olmayan ayarlara örnekler:

<xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>\
<xref:System.Xaml.XamlReaderSettings.BaseUri%2A>\
<xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>\
<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>\
<xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>.

Varsayılan okuyucu <xref:System.Xaml.XamlServices> için. <xref:System.Xaml.XamlXmlReader> Kendi <xref:System.Xaml.XamlXmlReader> ayarlarınızı sağlarsanız, varsayılan olmayan ı ayarlamak <xref:System.Xaml.XamlXmlReaderSettings>için aşağıdaki özellikler şunlardır:

<xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>

## <a name="parse"></a>Ayrıştır

<xref:System.Xaml.XamlServices.Parse%2A>xaml girişi bir XAML düğüm akışı oluşturan bir yük yolu API `Load` olduğu gibi. Ancak, bu durumda, XAML girişi doğrudan yüklemek için tüm XAML içeren bir dize olarak sağlanır. <xref:System.Xaml.XamlServices.Parse%2A>çerçeve senaryolarından çok uygulama senaryoları için daha uygun olan hafif bir yaklaşımdır. Daha fazla bilgi için bkz. <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A>sadece bir iç <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> içeren sarılmış <xref:System.IO.StringReader> bir çağrıdır.

## <a name="save"></a>Kaydet

Kaydet yolunu <xref:System.Xaml.XamlServices.Save%2A> n çeşitli aşırı yüklemeler uygulayın. Tüm <xref:System.Xaml.XamlServices.Save%2A> yöntemlerin tümü bir nesne grafiğini giriş olarak alır ve <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> akış, dosya veya örnek olarak çıktı üretir.

Giriş nesnesinin bazı nesne gösteriminin kök nesnesi olması beklenir. Bu, bir iş nesnesinin tek kökü, bir Web-oI senaryosundaki bir sayfa için nesne ağacının kökü, tasarım aracından çalışan düzenleme yüzeyi veya senaryolar için uygun olan diğer kök nesne kavramları olabilir.

Birçok senaryoda, kaydettiğiniz nesne ağacı, bir çerçeve/uygulama modeli tarafından <xref:System.Xaml.XamlServices.Load%2A> uygulanan diğer API'lerle veya XAML yüklenen özgün bir işlemle ilişkilidir. Nesne ağacında yakalanan ve durum değişiklikleri, uygulamanızın çalışma zamanı ayarlarını kullanıcıdan yakaladığı değişiklikler, xaml'ı değiştirmiş olabilir, çünkü uygulamanız XAML tasarım yüzeyi, vb. Değişiklikli veya değişikliksiz, önce biçimlendirmeden XAML yükleme ve sonra tekrar kaydetme ve iki XAML biçimlendirme formunu karşılaştırma kavramı bazen XAML'nin gidiş-dönüş gösterimi olarak adlandırılır.

Biçimlendirme biçiminde ayarlanan karmaşık bir nesneyi kaydetme ve seri hale getirmenin zorluğu, xaml'ı daha az okunabilir kılan tam temsil arasında bir denge sağlamaktır. Ayrıca, XAML için farklı müşteriler, bu bakiyenin nasıl ayarlanması gerektiğine ilişkin farklı tanımlara veya beklentilere sahip olabilir. API'ler <xref:System.Xaml.XamlServices.Save%2A> bu dengenin bir tanımını temsil ediyor. API'ler, <xref:System.Xaml.XamlServices.Save%2A> belirli XAML düğüm akışı yapılarının biçimlendirmeye geri kaydedildiğinde nerede optimize edilebileceğini belirlemek için kullanılabilir XAML şeması bağlamını ve varsayılan CLR tabanlı , <xref:System.Xaml.XamlType>ve <xref:System.Xaml.XamlMember>diğer XAML içsel ve XAML türü sistem kavramlarıözelliklerini kullanır. Örneğin, <xref:System.Xaml.XamlServices> save yolları nesneler için çözmek <xref:System.Xaml.XamlType> için CLR tabanlı varsayılan XAML şema <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>bağlamını kullanabilir, bir , belirleyebilir ve özelliği nesnenin XAML içeriğine yazdıklarında özellik öğesi etiketlerini atlayabilir.

<a name="transform"></a>
## <a name="transform"></a>Dönüşüm

<xref:System.Xaml.XamlServices.Transform%2A>bir yük yolunu ve kaydetme yolunu tek bir işlem olarak bağlayarak XAML'yi dönüştürür veya dönüştürür. Farklı bir şema bağlamı veya farklı bir <xref:System.Xaml.XamlReader> <xref:System.Xaml.XamlWriter>destek türü sistemi için kullanılabilir ve , hangi neden ortaya çıkan XAML dönüştürülür etkiler. Bu, geniş dönüştürme işlemleri için iyi çalışır.

XAML düğüm akışındaki her düğümün incelenmesine dayanan işlemler için genellikle <xref:System.Xaml.XamlServices.Transform%2A>. Bunun yerine kendi yük yolu kaydetme yol işlem serisini tanımlamanız ve kendi mantığınızı müdahale etmeniz gerekir. Yollardan birinde, kendi düğüm döngünüzün etrafında bir XAML okuyucu/XAML yazar çifti kullanın. Örneğin, ilk XAML'yi <xref:System.Xaml.XamlXmlReader> kullanarak yükleyin ve ardışık <xref:System.Xaml.XamlXmlReader.Read%2A> çağrılarla düğümlere adım atın. XAML düğüm akışı düzeyinde çalışan artık bir dönüşüm uygulamak için tek tek düğümleri (türleri, üyeler, diğer düğümler) ayarlayabilir veya düğümü olduğu gibi bırakabilirsiniz. Ardından düğümü a'nın `Write` <xref:System.Xaml.XamlObjectWriter> ilgili API'sine gönderir ve nesneyi yazarsınız. Daha fazla bilgi için Bkz. [XAML Düğüm Akışı Yapılarını ve Kavramlarını Anlama.](understanding-xaml-node-stream-structures-and-concepts.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [XAML Hizmetleri](../../../api/index.md)
