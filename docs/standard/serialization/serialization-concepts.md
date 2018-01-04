---
title: "Seri hale getirme kavramları"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76946ed1b714ba0bd01c79bb772524c84cf8b2ca
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="serialization-concepts"></a>Seri hale getirme kavramları
Neden serileştirme kullanmak istiyor? İki en önemli bir tam kopya daha sonraki bir aşamada yeniden oluşturulabilir için bir depolama ortamına bir nesne durumunu sürdürülmesi için ve nesne değerine göre bir uygulama etki alanından diğerine gönderilecek nedenleridir. Örneğin, serileştirme ASP.NET oturum durumu Kaydet ve Pano'ya Windows Forms nesneleri kopyalamak için kullanılır. Bu aynı zamanda nesneleri değerine göre bir uygulama etki alanından diğerine geçmesine uzaktan iletişim tarafından kullanılır.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Kalıcı depolama
Genellikle, disk ve daha sonra daha sonra bu verileri almak için bir nesne alanları değeri depolamak gereklidir. Bu seri hale getirme üzerinde kullanmadan elde etmek kolay bu yaklaşım genellikle kullanışsız olsa da ve hataya ve nesneleri hiyerarşisini izlemek gerektiğinde giderek daha karmaşık hale gelir. Nesneleri binlerce içeren bir büyük iş uygulaması yazma ve Kaydet ve alanlar ve özellikler için ve her nesne için diskten geri yüklemek için kod yazmadan düşünün. Serileştirme bu amaç elde etmek için kullanışlı bir mekanizma sağlar.

Ortak dil çalışma zamanı nesneleri bellekte nasıl depolandığını yönetir ve otomatik seri hale getirme mekanizmasını kullanarak sağlar [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md). Bir nesne seri olduğunda, sınıf, derleme ve tüm veri üyeleri sınıf örneği adı için depolama yazılır. Üye değişkenleri genellikle depolama başvurularının diğer örnekleri nesneleri. Sınıf serileştirildiğinde serileştirme motoruna zaten, aynı nesne birden çok kez serileştirilmemiş emin olmak için seri hale getirilmiş başvurulan nesneleri izler. İle sağlanan serileştirme mimarisi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] doğru işleyen grafikler ve döngüsel başvurulara otomatik olarak nesnesi. Nesne grafiklerde yerleştirilen yalnızca serileştirilmiş nesne tarafından başvurulan tüm nesnelerin aynı zamanda olarak işaretlenmiş olmalıdır gereksinimdir `Serializable` (daha fazla bilgi için bkz: [temel serileştirme](basic-serialization.md)). Bu yapılmadığı, işaretsiz nesneyi serileştirmek seri hale getirici girişiminde bulunduğunda bir özel durum.

Serileştirilmiş sınıfı seri sınıfı yeniden oluşturulur ve tüm veri üyelerinin değerlerini otomatik olarak geri yüklenir.

## <a name="marshal-by-value"></a>Değere göre sıralama
Nesneleri oluşturulan burada yalnızca uygulama etki alanında geçerli değil. Nesne türetilen sürece girişimleri nesnesini parametre olarak geçirme veya onu döndürmek için sonuç olarak başarısız olur `MarshalByRefObject` olarak işaretlenebilir veya `Serializable`. Nesne olarak işaretlenmişse `Serializable`, nesne otomatik olarak ayarlanır seri hale getirilmiş bir uygulama etki alanından diğerine taşınan ve ikinci uygulama etki alanı nesnesinde tam bir kopyasını oluşturmak için seri durumdan. Bu işlem genellikle hazırlanır tarafından değeri olarak adlandırılır.
 
Bir nesneyi zaman türetilen `MarshalByRefObject`, bir nesne başvurusu nesne yerine başka bir uygulama etki alanına geçirilir. Türetilen bir nesne de işaretleyebilirsiniz `MarshalByRefObject` olarak `Serializable`. Remoting, bir yedek Seçici ile önceden yapılandırılmış serileştirme sorumlu biçimlendirici ile birlikte bu nesne kullanıldığında (`SurrogateSelector`), seri hale getirme işlemi denetimini alır ve türetilen tüm nesneleri değiştirir `MarshalByRefObject` ile bir proxy. Olmadan `SurrogateSelector` yerinde serileştirme mimarisi açıklanan standart seri hale getirme kurallara [seri hale getirme işleminde adımları](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>İlgili bölümler  
 [İkili Serileştirme](../../../docs/standard/serialization/binary-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği ikili serileştirme mekanizması açıklanmaktadır.  
  
 [Uzak nesneleri](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 Çeşitli iletişimleri .NET Framework için kullanılabilecek yöntemleri Uzaktan iletişimler açıklar.  
  
 [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği XML ve SOAP serileştirme mekanizması açıklanmaktadır.
