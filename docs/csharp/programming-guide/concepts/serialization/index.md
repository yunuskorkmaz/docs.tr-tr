---
title: Serileştirme (C# )
ms.date: 01/02/2020
ms.openlocfilehash: d914298a370b09307e84c88959542b4823cf37ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167601"
---
# <a name="serialization-c"></a>Serileştirme (C# )

Serileştirme, nesneyi depolamak veya belleğe, veritabanına veya dosyaya iletmek için nesneyi bayt akışına dönüştürme işlemidir. Temel amacı gerektiğinde yeniden oluşturabilmek için bir nesnenin durumunu kaydetmektir. Ters işlem deserialization denir.

## <a name="how-serialization-works"></a>Serileştirme nasıl çalışır?

Bu resimde serileştirme genel süreci gösterir:

![Serileştirme grafiği](./media/index/serialization-process.gif)

Nesne, verileri taşıyan bir akışa seri hale getirilir. Akış, nesnenin sürümü, kültürü ve derleme adı gibi türü hakkında da bilgilere sahip olabilir. Bu akıştan, nesne bir veritabanında, dosyada veya bellekte depolanabilir.

### <a name="uses-for-serialization"></a>Serileştirme için kullanım alanları

Serileştirme, geliştiricinin nesnenin durumunu kaydetmesine ve gerektiğinde yeniden oluşturmasına olanak sağlayarak nesnelerin depolanmasını ve veri alışverişini sağlar. Serileştirme yoluyla, bir geliştirici gibi eylemler gerçekleştirebilir:

* Web hizmeti kullanarak nesneyi uzak bir uygulamaya gönderme
* Bir nesneyi bir etki alanından diğerine geçirme
* Nesneyi güvenlik duvarından JSON veya XML dizesi olarak geçirme
* Uygulamalar arasında güvenlik veya kullanıcıya özel bilgilerin korunması

## <a name="json-serialization"></a>JSON seri hale getirme

Ad <xref:System.Text.Json> alanı JavaScript Nesne Gösterimi (JSON) serileştirme ve deserialization için sınıflar içerir. JSON, web genelinde veri paylaşımı için yaygın olarak kullanılan açık bir standarttır.

JSON serileştirme, bir nesnenin ortak özelliklerini [RFC 8259 JSON belirtimine](https://tools.ietf.org/html/rfc8259)uygun bir dize, bayt dizisi veya akışa serileştirir. Sınıfın bir <xref:System.Text.Json.JsonSerializer> örneğini serileştirme veya deserialize etme biçimini denetlemek için:

* <xref:System.Text.Json.JsonSerializerOptions> Nesne kullanma
* Ad alanından <xref:System.Text.Json.Serialization> sınıflara veya özelliklere öznitelikleri uygulama
* [Özel dönüştürücüler uygulayın](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>İkili ve XML serileştirme

Ad <xref:System.Runtime.Serialization> alanı ikili ve XML serileştirme ve deserialization için sınıflar içerir.

İkili serileştirme, depolama veya soket tabanlı ağ akışları gibi kullanımlar için kompakt serileştirme üretmek için ikili kodlama kullanır. İkili serileştirmede, salt okunur olan tüm üyeler bile seri hale getirilir ve performans artar.

XML serileştirme, bir nesnenin ortak alanlarını ve özelliklerini veya yöntemlerin parametrelerini ve döndürme değerlerini belirli bir XML Şema tanım dili (XSD) belgesine uygun bir XML akışına serileştirir. XML serileştirme, ortak özelliklere ve XML'e dönüştürülen alanlara sahip güçlü bir şekilde yazılan sınıflara neden olur. <xref:System.Xml.Serialization>XML'i seri hale getirme ve deserialize etme sınıfları içerir. Sınıfın bir örneğini <xref:System.Xml.Serialization.XmlSerializer> serileştirme veya deserialize etme biçimini denetlemek için sınıflara ve sınıf üyelerine öznitelikleri uygularsınız.

### <a name="making-an-object-serializable"></a>Nesneyi serileştirilebilir hale getirme

İkili veya XML serileştirme için şunları yapmanız gerekir:

* Seri hale getirilecek nesne
* Serileştirilmiş nesneyi içeren bir akış
* Bir <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> örnek

<xref:System.SerializableAttribute> Tür örnekleriseriolabilir belirtmek için bir tür öznitelik uygulayın. Serihale getirmeye çalışırsanız, ancak tür özniteliği yoksa <xref:System.SerializableAttribute> bir özel durum atılır.

Bir alanın seri hale getirilen <xref:System.NonSerializedAttribute> olmasını önlemek için özniteliği uygulayın. Serileştirilebilir türde bir alan, belirli bir ortama özgü bir işaretçi, tutamaç veya başka bir veri yapısı içeriyorsa ve alan anlamlı bir şekilde farklı bir ortamda yeniden oluşturulamıyorsa, bunu seri dışı hale getirmek isteyebilirsiniz.

Serileştirilmiş bir sınıf işaretli <xref:System.SerializableAttribute>diğer sınıfların nesnelerine başvurular içeriyorsa, bu nesneler de seri hale getirilir.

### <a name="basic-and-custom-serialization"></a>Temel ve özel serileştirme

İkili ve XML serileştirme, temel ve özel olmak üzere iki şekilde gerçekleştirilebilir.

Temel serileştirme, nesneyi otomatik olarak serihale getirmek için .NET Framework'u kullanır. Tek gereksinim, sınıfın <xref:System.SerializableAttribute> özniteliğinin uygulanmasıdır. Belirli <xref:System.NonSerializedAttribute> alanların seri hale getirilen olmasını engellemek için kullanılabilir.

Temel serileştirme yi kullandığınızda, nesnelerin sürümü sorunlara neden olabilir. Sürüm sorunları önemli olduğunda özel serileştirme kullanırsınız. Temel serileştirme, serileştirme gerçekleştirmenin en kolay yoludur, ancak işlem üzerinde çok fazla denetim sağlamaz.

Özel serileştirmede, tam olarak hangi nesnelerin serihale edileceğini ve nasıl yapılacağını belirtebilirsiniz. Sınıf işaretlenmeli <xref:System.SerializableAttribute> ve <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulamalı. Nesnenizin de özel bir şekilde deserialized olmasını istiyorsanız, özel bir oluşturucu kullanın.

## <a name="designer-serialization"></a>Tasarımcı serileştirme

Tasarımcı serileştirme, geliştirme araçlarıyla ilişkili nesne kalıcılığı türünü içeren özel bir serileştirme biçimidir. Tasarımcı serileştirme, nesne grafiğini daha sonra nesne grafiğini kurtarmak için kullanılabilecek bir kaynak dosyaya dönüştürme işlemidir. Kaynak dosya kod, biçimlendirme ve hatta SQL tablo bilgilerini içerebilir.

## <a name="BKMK_RelatedTopics"></a>İlgili Konular ve Örnekler  

[System.Text.Json genel bakış](../../../../standard/serialization/system-text-json-overview.md) Kütüphanenin nasıl `System.Text.Json` alındığını gösterir.

[JSON'u .NET'te seri hale getirmek ve deserialize etmek için .](../../../../standard/serialization/system-text-json-how-to.md)
<xref:System.Text.Json.JsonSerializer> Sınıfı kullanarak JSON'a nesne verilerinin nasıl okunup yazılabildiğini gösterir.

[İzleme: Visual Studio'da Bir Nesneyi Kalıcıyor (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Serileştirmenin, bir nesnenin verilerini örnekler arasında kalıcı hale getirmek için nasıl kullanılabileceğini gösterir ve nesne bir sonraki anında olduğunda değerleri depolamanızı ve bunları almanızı sağlar.

[XML dosyasından nesne verileri nasıl okunur (C#)](how-to-read-object-data-from-an-xml-file.md)  
Sınıfı kullanarak daha önce bir XML dosyasına yazılmış <xref:System.Xml.Serialization.XmlSerializer> nesne verilerinin nasıl okunduğunu gösterir.

[Bir XML dosyasına nesne verileri yazma (C#)](how-to-write-object-data-to-an-xml-file.md)  
<xref:System.Xml.Serialization.XmlSerializer> Sınıfı kullanarak nesnenin sınıftan bir XML dosyasına nasıl yazılsüreceğini gösterir.
