---
title: Serileştirme (C# )
ms.date: 01/02/2020
ms.openlocfilehash: 1d2bda9022b7e43744dd8a0286eff88914cf65a3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635736"
---
# <a name="serialization-c"></a>Serileştirme (C# )

Serileştirme, nesneyi depolamak veya belleği, bir veritabanı ya da bir dosyaya aktarmak için bir nesneyi bayt akışına dönüştürme işlemidir. Temel amacı, bir nesnenin durumunu gerektiğinde yeniden oluşturmak için kaydetmeyecektir. Ters işlem serisini kaldırma olarak adlandırılır.

## <a name="how-serialization-works"></a>Serileştirme çalışma şekli

Bu çizimde serileştirme işleminin genel işlemi gösterilmektedir:

![Serileştirme grafiği](./media/index/serialization-process.gif)

Nesne, verileri taşıyan bir akışa serileştirilir. Akışta Ayrıca nesnenin türü ile ilgili sürüm, kültür ve derleme adı gibi bilgiler de bulunabilir. Bu akıştan, nesne bir veritabanında, bir dosyada veya bellekte depolanabilir.

### <a name="uses-for-serialization"></a>Serileştirme için kullanımlar

Serileştirme, geliştiricinin bir nesnenin durumunu kaydetmesine ve gerektiğinde, nesnelerin ve veri değişim verilerinin depolanmasını sağlayarak yeniden oluşturmasını sağlar. Bir geliştirici, serileştirme aracılığıyla şunları gibi eylemler gerçekleştirebilir:

* Web hizmeti kullanarak nesneyi uzak uygulamaya gönderme
* Bir etki alanından diğerine nesne geçirme
* Bir nesneyi bir JSON veya XML dizesi olarak güvenlik duvarı üzerinden geçirme
* Uygulamalar arasında güvenlik veya kullanıcıya özel bilgileri koruma

## <a name="json-serialization"></a>JSON seri hale getirme

<xref:System.Text.Json> ad alanı, JavaScript Nesne Gösterimi (JSON) serileştirme ve serisini kaldırma için sınıflar içerir. JSON, web genelinde veri paylaşımında yaygın olarak kullanılan açık bir standarttır.

JSON serileştirme bir nesnenin ortak özelliklerini, [RFC 8259 JSON belirtimine](https://tools.ietf.org/html/rfc8259)uyan bir dizeye, bayt dizisine veya akışa seri hale getirir. <xref:System.Text.Json.JsonSerializer>, sınıfın bir örneğini seri hale getirmenin veya seri hale getirmenin yolunu denetlemek için:

* <xref:System.Text.Json.JsonSerializerOptions> nesnesi kullanma
* <xref:System.Text.Json.Serialization> ad alanından sınıflara veya özelliklere öznitelikleri uygulama
* [Özel dönüştürücüler uygulama](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>İkili ve XML serileştirme

<xref:System.Runtime.Serialization> ad alanı, ikili ve XML serileştirme ve seri durumdan çıkarma için sınıflar içerir.

İkili serileştirme, depolama veya soket tabanlı ağ akışları gibi kullanımlar için sıkıştırılmış serileştirme oluşturmak üzere ikili kodlama kullanır. İkili serileştirme ' de, salt okunan tüm Üyeler, hatta salt okunurdur ve performans geliştirilir. 

XML serileştirme, bir nesnenin ortak alanlarını ve özelliklerini veya parametrelerinin parametrelerini ve dönüş değerlerini belirli bir XML şeması tanım dili (XSD) belgesine uygun bir XML akışı olarak serileştirir. XML serileştirme, XML 'e dönüştürülen ortak özellikler ve alanlarla kesin olarak belirlenmiş sınıflarda oluşur. <xref:System.Xml.Serialization> XML serileştirme ve seri durumdan çıkarma için sınıflar içerir. Sınıfın bir örneğini seri hale getirmenin veya seri hale getirmenin <xref:System.Xml.Serialization.XmlSerializer> yolunu denetlemek için sınıflara ve sınıf üyelerine öznitelikler uygularsınız.

### <a name="making-an-object-serializable"></a>Bir nesneyi seri hale getirilebilir hale getirme

İkili veya XML serileştirme için şunlar gerekir:

* Seri hale getirilecek nesne
* Seri hale getirilen nesneyi içeren akış
* Bir <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> örneği

Türün örneklerinin seri hale getirilebilir olduğunu göstermek için <xref:System.SerializableAttribute> özniteliğini bir türe uygulayın. Seri hale getirme denerseniz, ancak türün <xref:System.SerializableAttribute> özniteliği yoksa bir özel durum oluşturulur.

Bir alanın serileştirilmesi için <xref:System.NonSerializedAttribute> özniteliğini uygulayın. Seri hale getirilebilir türdeki bir alan belirli bir ortama özel bir işaretçi, tanıtıcı veya başka bir veri yapısı içeriyorsa ve alan farklı bir ortamda anlamlı bir reconstituted değilse, bu durumda seri hale getirilebilir olmayan bir şekilde oluşturulabilir.

Serileştirilmiş bir sınıf, <xref:System.SerializableAttribute>olarak işaretlenen diğer sınıfların nesnelerine başvurular içeriyorsa, bu nesneler de serileştirilir.

### <a name="basic-and-custom-serialization"></a>Temel ve özel serileştirme

İkili ve XML serileştirme, temel ve özel olmak üzere iki şekilde gerçekleştirilebilir.

Temel serileştirme, nesneyi otomatik olarak seri hale getirmek için .NET Framework kullanır. Tek gereksinim, sınıfın <xref:System.SerializableAttribute> özniteliğin uygulanmış olması. <xref:System.NonSerializedAttribute>, belirli alanların serileştirilme tutulmasını sağlamak için kullanılabilir.

Temel serileştirme kullandığınızda nesnelerin sürümü oluşturma sorunlar oluşturabilir. Sürüm oluşturma sorunları önemli olduğunda özel serileştirme kullanırsınız. Temel serileştirme, serileştirme gerçekleştirmenin en kolay yoludur, ancak süreç üzerinde çok fazla denetim sağlamaz.

Özel seri hale getirmek için, tam olarak hangi nesnelerin serileştirildiği ve nasıl yapılacağını belirtebilirsiniz. Sınıfın <xref:System.SerializableAttribute> işaretlenmesi ve <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulamanız gerekir. Nesnenizin bir özel şekilde seri durumdan çıkarılabilmesini istiyorsanız özel bir Oluşturucu kullanın.

## <a name="designer-serialization"></a>Tasarımcı serileştirme

Tasarımcı serileştirme, geliştirme araçlarıyla ilişkili nesne kalıcılığı türünü içeren özel bir serileştirme biçimidir. Tasarımcı serileştirme bir nesne grafiğini, daha sonra nesne grafiğini kurtarmak için kullanılabilecek bir kaynak dosyaya dönüştürme işlemidir. Kaynak dosya, kod, biçimlendirme veya hatta SQL tablo bilgisi içerebilir.

## <a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler  

[System. Text. JSON genel bakış](../../../../standard/serialization/system-text-json-overview.md) `System.Text.Json` kitaplığının nasıl alınacağını gösterir.

[.Net 'TE JSON serileştirmek ve serisini kaldırma](../../../../standard/serialization/system-text-json-how-to.md). <xref:System.Text.Json.JsonSerializer> sınıfı kullanılarak JSON 'dan ve öğesinden nesne verilerinin nasıl okunacağını ve yazılacağını gösterir.

[İzlenecek yol: Visual Studio 'da bir nesneyi kalıcıC#hale getirme ()](walkthrough-persisting-an-object-in-visual-studio.md)  
Serileştirme 'in nesnelerin örnekleri arasında bir nesne verilerini kalıcı hale getirmek için nasıl kullanılabileceğini gösterir. Bu, değerleri depolamanızı ve nesnenin bir sonraki örneklendirilmesi durumunda bunları almanızı sağlar.

[XML dosyasından nesne verilerini okuma (C#)](how-to-read-object-data-from-an-xml-file.md)  
Daha önce <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerinin nasıl okunacağını gösterir.

[Nesne verilerini bir XML dosyasına yazma (C#)](how-to-write-object-data-to-an-xml-file.md)  
<xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanarak bir sınıftan XML dosyasına nesnenin nasıl yazılacağını gösterir.
