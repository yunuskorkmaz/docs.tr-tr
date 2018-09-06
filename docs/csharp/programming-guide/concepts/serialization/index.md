---
title: Seri hale getirme (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 7d72be92e5568037264438e3fde1e7565366c962
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858323"
---
# <a name="serialization-c"></a>Seri hale getirme (C#)

Serileştirme bir nesneyi depolamak veya bellek, bir veritabanı veya dosya aktarmak için bayt akışı bir nesne dönüştürme işlemidir. Ana amacı, gerektiğinde yeniden oluşturmak için bir nesnenin durumu kaydetmektir. Seri durumundan çıkarma ters işlem çağrılır.

## <a name="how-serialization-works"></a>Seri hale getirme nasıl çalışır?

Bu örnekte, genel işlem serileştirme gösterilmiştir.

![Grafik seri hale getirme](./media/serialization.gif "seri hale getirme")

Yalnızca veri ancak nesnenin türü, sürüm, kültür ve derleme adı gibi bilgileri izleme bir akışa nesne seri hale getirilir. Bu akıştan, bir veritabanı, dosya veya bellek içinde saklanabilir.

### <a name="uses-for-serialization"></a>Serileştirme kullanımları

Seri hale getirme geliştiricinin bir nesne durumunu kaydetmek ve gerektiğinde depolama nesneleri ve bunun yanı sıra veri değişimi sağlama yeniden sağlar. Serileştirme bir geliştirici nesnesi aracılığıyla bir Web hizmeti uzak bir uygulamaya gönderme, bir etki alanından bir nesne geçirme, nesnenin bir güvenlik duvarı üzerinden bir XML dizesi olarak geçirme veya güvenliğini sağlama gibi eylemleri gerçekleştirebilirsiniz veya uygulamalar arasında kullanıcıya özgü bilgileri.

### <a name="making-an-object-serializable"></a>Bir nesne seri hale getirilebilir yapma

Nesne seri hale için gereken bir nesneyi serileştirmek için bir akış serileştirilmiş nesne içerecek ve bir <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> seri hale getirme ve seri kaldırma nesneler için gerekli olan sınıflar içerir.

Uygulama <xref:System.SerializableAttribute> özniteliği bu türün örneğini serileştirilmiş göstermek için bir tür. Seri hale getirmek çalışır, ancak türüne sahip bir özel durum <xref:System.SerializableAttribute> özniteliği.

Seri hale getirilebilir olması için sınıf alana istemiyorsanız, uygulama <xref:System.NonSerializedAttribute> özniteliği. Bir işaretçi, tanıtıcı veya belirli bir ortama özgü bazı başka veri yapısına serializable bir tür alanı içeren ve alan atayamayacağına farklı bir ortamda yeniden oluşturulur olamaz, nonserializable yapmak isteyebilirsiniz.

Serileştirilmiş sınıf işaretlenen diğer sınıfların nesnelere başvurular içeriyorsa <xref:System.SerializableAttribute>, bu nesneleri ayrıca seri hale.

## <a name="binary-and-xml-serialization"></a>İkili ve XML serileştirme

İkili veya XML serileştirme kullanabilirsiniz. İkili seri hale getirme, tüm üyeleri, salt okunur bile üyeleri seri hale getirilmiş ve performans geliştirilir. XML serileştirme daha okunabilir bir kod ve nesneyi paylaşmak ve birlikte çalışabilirlik amacıyla kullanım daha fazla esneklik sağlar.

### <a name="binary-serialization"></a>İkili seri hale getirme

İkili kodlama ikili serileştirme depolama veya ağ yuva tabanlı akışları gibi kullanımlar için compact serileştirme üretmek için kullanır.

### <a name="xml-serialization"></a>XML serileştirme

XML serileştirme ortak alanları ve bir nesne veya özelliklerini parametre ve dönüş değerleri yöntemleri, belirli bir XML Şeması Tanım Dili (XSD) belge uyan bir XML akışı olarak serileştirir. XML serileştirme sonuçlarında sınıflarıyla ortak özellikler ve XML için dönüştürülür alanları kesin. <xref:System.Xml.Serialization> seri hale getirme ve XML seri durumdan çıkarmak için gereken sınıfların içerir.

Öznitelikleri için sınıflar ve sınıf üyeleri denetlenmesine uygulamak <xref:System.Xml.Serialization.XmlSerializer> serileştiren veya sınıfının bir örneği seri durumdan çıkarır.

## <a name="basic-and-custom-serialization"></a>Temel ve özel seri hale getirme

İki yolla temel ve özel serileştirme gerçekleştirilebilir. Temel serileştirme otomatik olarak nesneyi serileştirmek için .NET Framework'ü kullanır.

### <a name="basic-serialization"></a>Temel serileştirme

Nesne sahip temel serileştirme sırasında tek gereksinim olmasıdır <xref:System.SerializableAttribute> özniteliği uygulandı. <xref:System.NonSerializedAttribute> Serileştirilmekte olan belirli alanları tutmak için kullanılabilir.

Temel serileştirme kullandığınızda, sürüm oluşturma nesnelerin sorunlara neden olabilir. Sürüm oluşturma sorunları önemli olduğunda, özel serileştirme kullanırsınız. Temel serileştirme serileştirme gerçekleştirmek için en kolay yoludur ancak kadar denetim işlemi üzerinde sağlamaz.

### <a name="custom-serialization"></a>Özel serileştirme

Özel serileştirme, tam olarak hangi nesnelerin serileştirilmiş ve nasıl yapılacağıyla belirtebilirsiniz. Sınıf işaretlenmelidir <xref:System.SerializableAttribute> ve uygulama <xref:System.Runtime.Serialization.ISerializable> arabirimi.

Bir özel biçimde seri durumdan nesnenizin istiyorsanız özel bir oluşturucu kullanmanız gerekir.

## <a name="designer-serialization"></a>Tasarımcı serileştirme

Tasarımcı serileştirme özel bir geliştirme araçları ile ilişkili nesne Kalıcılık türü içeren serileştirme biçimidir. Tasarımcı serileştirme bir nesne grafiğinin daha sonra nesne grafiğini kurtarmak için kullanılabilir bir kaynak dosyasına dönüştürme işlemidir. Bir kaynak dosyası, kod, biçimlendirme veya hatta SQL tablo bilgileri içerebilir.

##  <a name="BKMK_RelatedTopics"></a> İlgili Konular ve örnekler  
[İzlenecek yol: Visual Studio'da (C#) bir nesneyi kalıcı kılma](walkthrough-persisting-an-object-in-visual-studio.md)  
Bir nesnenin veri değerleri depolamak ve bunları nesnesi örneği başlatıldığında almanıza imkan sağlayan, örnekleri arasında kalıcı hale getirmek için serileştirme'nın nasıl kullanılabileceğini gösterir.

[Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma](how-to-read-object-data-from-an-xml-file.md)  
 Bir XML dosyası kullanmayı önceden yazılmış nesne verilerini okuma işlemini gösterir <xref:System.Xml.Serialization.XmlSerializer> sınıfı.

[Nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma](how-to-write-object-data-to-an-xml-file.md)  
Nesne öğesinden bir sınıf bir XML kullanarak dosyaya yazma işlemi gösterilmektedir <xref:System.Xml.Serialization.XmlSerializer> sınıfı.
