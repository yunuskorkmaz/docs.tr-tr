---
title: Seri hale getirme (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 03a7cd2d48b79d94674e64e96130e20a86051fb2
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957859"
---
# <a name="serialization-c"></a>Seri hale getirme (C#)

Seri hale getirme bir nesne, nesne depolamak veya bellek, bir veritabanı veya dosya aktarmak için baytı bir akışa dönüştürme işlemidir. Asıl amacı, gerektiğinde yeniden oluşturmak için bir nesnenin durumu tasarruf etmektir. Ters işlemi seri durumdan çıkarma adı verilir.

## <a name="how-serialization-works"></a>Seri hale getirme nasıl çalışır?

Bu çizim serileştirme genel işlemi gösterilmektedir.

![Serileştirme Grafiği](./media/serialization.gif "seri hale getirme")

Yalnızca veri ancak sürüm, kültür ve derleme adı gibi nesnenin türü hakkında bilgi taşıyan bir akışa nesne seri. Bu akıştan, bir veritabanı, bir dosya veya bellek depolanabilir.

### <a name="uses-for-serialization"></a>Serileştirme için de kullanır

Seri hale getirme bir nesnenin durumunu kaydetmek ve gerekirse, veri değişimi yanı sıra nesneleri depolama sağlama yeniden oluşturmak geliştiricinin sağlar. Seri hale getirme bir geliştirici nesne uzak uygulama için bir Web hizmeti aracılığıyla gönderme, bir nesne bir etki alanından diğerine geçirme, bir nesne bir güvenlik duvarı üzerinden XML dizesi olarak geçirme veya güvenliğini sağlama gibi eylemleri gerçekleştirebilir veya uygulamalar arasında kullanıcıya özgü bilgileri.

### <a name="making-an-object-serializable"></a>Bir nesne seri hale getirilebilir yapma

Nesnenin seri hale getirilebilmesi için ihtiyacınız nesneyi serileştirmek için akış serileştirilmiş nesne içeren bir ve bir <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> seri hale getirme ve nesneleri seri durumdan çıkarmak için gerekli olan sınıflar içerir.

Uygulama <xref:System.SerializableAttribute> özniteliği, bu türdeki örneklerin serileştirilebilir belirtmek için bir tür. Seri hale getirmek dener, ancak türü yok bir özel durum <xref:System.SerializableAttribute> özniteliği.

Seri hale getirilebilir sınıfınız bir alanı istemiyorsanız, uygulama <xref:System.NonSerializedAttribute> özniteliği. Seri hale getirilebilir türünde bir alan bir işaretçi, bir tanıtıcı ya da belirli bir ortama özgü bazı bir veri yapısı içeren ve alan anlamlı farklı bir ortamda reconstituted olamaz, nonserializable yapmak isteyebilirsiniz.

Seri hale getirilmiş bir sınıf işaretlenen diğer sınıfların nesnelerini başvurular içeriyorsa <xref:System.SerializableAttribute>, bu nesneler de seri hale getirilir.

## <a name="binary-and-xml-serialization"></a>İkili ve XML serileştirme

İkili veya XML serileştirme kullanabilirsiniz. İkili seri hale getirme, tüm üyeleri, salt okunur bile üyeleri serileştirilir ve performansı geliştirilmiştir. XML serileştirme, daha okunabilir kod ve nesne paylaşımı ve birlikte çalışabilirlik amacıyla kullanımı daha fazla esneklik sağlar.

### <a name="binary-serialization"></a>İkili seri hale getirme

İkili seri hale getirme, depolama veya ağ yuva tabanlı akışları gibi kullanımlar için compact serileştirme üretmek için ikili kodlama kullanır.

### <a name="xml-serialization"></a>XML serileştirme

XML serileştirme, belirli bir XML Şeması Tanım Dili (XSD) belge uyan bir XML akışı içine genel alanlar ve bir nesne veya özelliklerini parametreler ve dönüş değerleri yöntemlerden serileştirir. XML serileştirme sonuçlarında genel özellikleri ve XML biçimine dönüştürülür alanları sınıflarıyla kesin türü belirtilmiş. <xref:System.Xml.Serialization> seri hale getirme ve XML seri durumdan çıkarmak için gerekli olan sınıflar içerir.

Sınıfları ve sınıf üyeleri şeklini denetlemek için öznitelikleri uygulamak <xref:System.Xml.Serialization.XmlSerializer> serileştiren veya sınıfının bir örneği seri durumdan çıkarır.

## <a name="basic-and-custom-serialization"></a>Temel ve özel seri hale getirme

İki yolla temel ve özel serileştirme gerçekleştirilebilir. Temel serileştirme .NET Framework otomatik olarak nesneyi serileştirmek için kullanır.

### <a name="basic-serialization"></a>Temel seri hale getirme

Yalnızca temel serileştirmede nesnesinde olduğunu gereksinimdir <xref:System.SerializableAttribute> özniteliği uygulanmıştır. <xref:System.NonSerializedAttribute> Seri hale belirli alanları korumak için kullanılabilir.

Temel serileştirme kullandığınızda, nesnelerin sürüm sorunlara neden olabilir. Sürüm oluşturma sorunları önemli olduğunda özel serileştirme kullanırsınız. Temel serileştirme serileştirme gerçekleştirmek için en kolay yoludur ancak işlem üzerinde kadar denetim sağlamaz.

### <a name="custom-serialization"></a>Özel seri hale getirme

İçinde özel serileştirme, tam olarak hangi nesneleri seri hale getirilir ve nasıl yapılacağıyla belirtebilirsiniz. Sınıf işaretlenmelidir <xref:System.SerializableAttribute> ve uygulamanıza <xref:System.Runtime.Serialization.ISerializable> arabirimi.

Bir özel biçimde seri durumdan çıkarılacak nesnenizin istiyorsanız, bir özel Oluşturucu kullanmanız gerekir.

## <a name="designer-serialization"></a>Tasarımcı seri hale getirme

Tasarımcı serileştirme geliştirme araçları ile ilişkili nesne Kalıcılık türü içerir serileştirme özel biçimidir. Tasarımcı serileştirme bir nesne grafiğinin nesne grafiğinin kurtarmak için daha sonra kullanılabilir bir kaynak dosyasına dönüştürme işlemidir. Bir kaynak dosyası kodu, biçimlendirme veya hatta SQL tablo bilgileri içerebilir.

##  <a name="BKMK_RelatedTopics"></a> İlgili Konular ve örnekler  
[İzlenecek yol: Visual Studio'da (C#) bir nesneyi kalıcı kılma](walkthrough-persisting-an-object-in-visual-studio.md)  
Bir nesnenin veri değerlerini depolamak ve nesne örneği sonraki açışınızda almak sağlayarak örnekleri arasında kalıcı hale getirmek için seri hale getirme'nın nasıl kullanılabileceğini gösterir.

[Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma](how-to-read-object-data-from-an-xml-file.md)  
 Daha önce bir XML dosyası kullanmaya yazıldı nesne verilerini okuma gösterilmektedir <xref:System.Xml.Serialization.XmlSerializer> sınıfı.

[Nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma](how-to-write-object-data-to-an-xml-file.md)  
Bir XML dosyası kullanarak bir sınıftan nesne yazmak gösterilmiştir <xref:System.Xml.Serialization.XmlSerializer> sınıfı.
