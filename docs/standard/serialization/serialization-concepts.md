---
title: Serileştirme kavramları
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: 1a7fa7c3e5561fc9e48cf627a703abc747a72ba0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159838"
---
# <a name="serialization-concepts"></a>Serileştirme kavramları
Neden serileştirme kullanmak istiyor? İki en önemli bir tam kopya daha sonraki bir aşamada yeniden oluşturulabilir için bir depolama ortamına bir nesne durumunu sürdürülmesi için ve nesne değerine göre bir uygulama etki alanından diğerine gönderilecek nedenleridir. Örneğin, serileştirme ASP.NET oturum durumu Kaydet ve Pano'ya Windows Forms nesneleri kopyalamak için kullanılır. Bu aynı zamanda nesneleri değerine göre bir uygulama etki alanından diğerine geçmesine uzaktan iletişim tarafından kullanılır.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Kalıcı depolama
Genellikle bir nesnenin alanlarının değerini diske depolamak ve daha sonra bu verileri almak için gereklidir. Bu yaklaşım, serileştirme 'e bağlı kalmadan elde etmek kolaydır, ancak bir dizi nesnenin hiyerarşisini izlemeniz gerektiğinde giderek daha karmaşık hale gelir. Nesneleri binlerce içeren bir büyük iş uygulaması yazma ve Kaydet ve alanlar ve özellikler için ve her nesne için diskten geri yüklemek için kod yazmadan düşünün. Serileştirme bu amaç elde etmek için kullanışlı bir mekanizma sağlar.

Ortak dil çalışma zamanı, nesnelerin bellekte nasıl depolandığını yönetir ve [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)kullanarak otomatikleştirilmiş bir serileştirme mekanizması sağlar. Bir nesne seri olduğunda, sınıf, derleme ve tüm veri üyeleri sınıf örneği adı için depolama yazılır. Üye değişkenleri genellikle depolama başvurularının diğer örnekleri nesneleri. Sınıf serileştirildiğinde, serileştirme altyapısı, aynı nesnenin birden çok kez serileştirilmemesini sağlamak için başvurulan nesneleri izler, zaten serileştirilir. .NET Framework ile birlikte sunulan serileştirme mimarisi, nesne grafiklerini ve döngüsel başvuruları otomatik olarak işler. Nesne grafiklerde yer alan tek gereksinim, serileştirilmiş nesne tarafından başvurulan tüm nesnelerin de `Serializable` olarak işaretlenmesi gerekir (daha fazla bilgi için bkz. [temel serileştirme](basic-serialization.md)). Bu yapılmadığı, işaretsiz nesneyi serileştirmek seri hale getirici girişiminde bulunduğunda bir özel durum.

Serileştirilmiş sınıf seri durumdan çıkarılmışsa, sınıf yeniden oluşturulur ve tüm veri üyelerinin değerleri otomatik olarak geri yüklenir.

## <a name="marshal-by-value"></a>Değere göre sıralama
Nesneleri oluşturulan burada yalnızca uygulama etki alanında geçerli değil. Nesneyi bir parametre olarak geçirme veya sonuç olarak döndürme girişimleri, nesne `MarshalByRefObject` türetilmediği veya `Serializable`olarak işaretlendiğinden başarısız olur. Nesne `Serializable`olarak işaretlenmişse, nesne otomatik olarak serileştirilir, bir uygulama etki alanından diğerine taşınır ve sonra ikinci uygulama etki alanında nesnenin tam bir kopyasını oluşturmak için serisi kaldırılır. Bu işlem genellikle hazırlanır tarafından değeri olarak adlandırılır.

Bir nesne `MarshalByRefObject`türetilirse, nesne başvurusu nesnenin kendisi yerine bir uygulama etki alanından diğerine geçirilir. Ayrıca, `MarshalByRefObject` türetilen bir nesneyi `Serializable`olarak işaretleyebilirsiniz. Bu nesne, uzaktan iletişim ile kullanıldığında, bir vekil seçici (`SurrogateSelector`) ile önceden yapılandırılmış serileştirme işleminden sorumlu olan biçimlendirici, serileştirme işleminin denetimini alır ve `MarshalByRefObject` türetilen tüm nesneleri bir ara sunucu ile değiştirir. `SurrogateSelector` olmadan serileştirme mimarisi, [serileştirme Işlemindeki adımlarda](steps-in-the-serialization-process.md)açıklanan standart serileştirme kurallarını izler.  

## <a name="related-sections"></a>İlgili bölümler  
 [İkili Serileştirme](../../../docs/standard/serialization/binary-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği ikili serileştirme mekanizması açıklanmaktadır.  
  
 [.NET uzaktan iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
 Çeşitli iletişimleri .NET Framework için kullanılabilecek yöntemleri Uzaktan iletişimler açıklar.  
  
 [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği XML ve SOAP serileştirme mekanizması açıklanmaktadır.
