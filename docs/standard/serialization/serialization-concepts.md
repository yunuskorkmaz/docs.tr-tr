---
title: Serileştirme kavramları
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: 649c4475aa8dcfc657b7591a0068dbfa4af918ca
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976544"
---
# <a name="serialization-concepts"></a>Serileştirme kavramları
Neden serileştirme kullanmak istiyor? İki en önemli bir tam kopya daha sonraki bir aşamada yeniden oluşturulabilir için bir depolama ortamına bir nesne durumunu sürdürülmesi için ve nesne değerine göre bir uygulama etki alanından diğerine gönderilecek nedenleridir. Örneğin, serileştirme ASP.NET oturum durumu Kaydet ve Pano'ya Windows Forms nesneleri kopyalamak için kullanılır. Bu aynı zamanda nesneleri değerine göre bir uygulama etki alanından diğerine geçmesine uzaktan iletişim tarafından kullanılır.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Kalıcı depolama
Genellikle, disk ve ardından, daha sonra bu verileri almak için bir nesne alanlarının değeri depolamak gereklidir. Bu seri hale getirme üzerinde bağlı olmadan elde etmek kolay olsa da bu sık hantal yaklaşımdır ve hataya ve nesneleri hiyerarşisini izlemek gerektiğinde giderek daha karmaşık hale gelir. Nesneleri binlerce içeren bir büyük iş uygulaması yazma ve Kaydet ve alanlar ve özellikler için ve her nesne için diskten geri yüklemek için kod yazmadan düşünün. Serileştirme bu amaç elde etmek için kullanışlı bir mekanizma sağlar.

Ortak dil çalışma zamanı nesneleri bellekte nasıl depolanır yöneten ve kullanarak bir otomatik serileştirme mekanizması sağlar [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md). Bir nesne seri olduğunda, sınıf, derleme ve tüm veri üyeleri sınıf örneği adı için depolama yazılır. Üye değişkenleri genellikle depolama başvurularının diğer örnekleri nesneleri. Sınıf serileştirilmiş olduğunda, serileştirme motoruna zaten, aynı nesne birden çok kez serileştirildiği değil emin olmak için seri başvurulan nesneleri izler. İle sağlanan serileştirme mimarisi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] doğru işleyen grafikler ve döngüsel başvurulara otomatik olarak nesnesi. Serileştirilmiş nesne tarafından başvurulan tüm nesneleri olarak da işaretlenmelidir nesne grafikler üzerinde yerleştirilen tek gereksinim olmasıdır `Serializable` (daha fazla bilgi için [temel serileştirme](basic-serialization.md)). Bu yapılmadığı, işaretsiz nesneyi serileştirmek seri hale getirici girişiminde bulunduğunda bir özel durum.

Serileştirilmiş sınıfı seri durumdan sınıf yeniden ve tüm veri üyelerinin değerlerini otomatik olarak geri yüklenir.

## <a name="marshal-by-value"></a>Değere göre sıralama
Nesneleri oluşturulan burada yalnızca uygulama etki alanında geçerli değil. Nesne öğesinden türer sürece her türlü girişim nesne parametre olarak geçir veya bu döndürmek için sonuç olarak başarısız `MarshalByRefObject` veya olarak işaretlenmiş `Serializable`. Nesne olarak işaretlenmişse `Serializable`, otomatik olarak nesne olacak seri, bir uygulama etki alanından diğer taşınan ve ikinci uygulama etki alanındaki nesnenin tam bir kopyasını oluşturmak için seri durumdan. Bu işlem genellikle hazırlanır tarafından değeri olarak adlandırılır.
 
Bir nesneyi zaman türetilir `MarshalByRefObject`, bir nesne başvurusu nesne yerine başka bir uygulama etki alanına geçirilir. Türetilen bir nesne da işaretleyebilirsiniz `MarshalByRefObject` olarak `Serializable`. Bu nesne kullanıldığında uzaktan iletişim, bir vekil Seçici ile önceden yapılandırılmış seri hale getirme, sorumlu biçimlendirici (`SurrogateSelector`), seri hale getirme işlemi denetimini alır ve türetilen tüm nesneleri değiştirir `MarshalByRefObject` ile bir ara sunucu. Olmadan `SurrogateSelector` yerinde, serileştirme mimarisi açıklanan standart serileştirme kurallara [seri hale getirme işleminde adımları](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>İlgili bölümler  
 [İkili Serileştirme](../../../docs/standard/serialization/binary-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği ikili serileştirme mekanizması açıklanmaktadır.  
  
 [.NET uzaktan iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
 Çeşitli iletişimleri .NET Framework için kullanılabilecek yöntemleri Uzaktan iletişimler açıklar.  
  
 [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği XML ve SOAP serileştirme mekanizması açıklanmaktadır.
