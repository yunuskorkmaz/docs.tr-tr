---
title: Serileştirme kavramları
description: Serileştirme bir nesnenin durumunu yakalamak veya bir uygulama etki alanından diğerine bir nesne değere göre göndermek için kullanılabilir.
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: a185855f4b6913c8e1d57bf36fc5c37411123e68
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541206"
---
# <a name="serialization-concepts"></a>Serileştirme kavramları
Neden serileştirme kullanmak istiyor? İki en önemli bir tam kopya daha sonraki bir aşamada yeniden oluşturulabilir için bir depolama ortamına bir nesne durumunu sürdürülmesi için ve nesne değerine göre bir uygulama etki alanından diğerine gönderilecek nedenleridir. Örneğin, serileştirme ASP.NET oturum durumu Kaydet ve Pano'ya Windows Forms nesneleri kopyalamak için kullanılır. Bu aynı zamanda nesneleri değerine göre bir uygulama etki alanından diğerine geçmesine uzaktan iletişim tarafından kullanılır.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Kalıcı depolama
Genellikle bir nesnenin alanlarının değerini diske depolamak ve daha sonra bu verileri almak için gereklidir. Bu yaklaşım, serileştirme 'e bağlı kalmadan elde etmek kolaydır, ancak bir dizi nesnenin hiyerarşisini izlemeniz gerektiğinde giderek daha karmaşık hale gelir. Nesneleri binlerce içeren bir büyük iş uygulaması yazma ve Kaydet ve alanlar ve özellikler için ve her nesne için diskten geri yüklemek için kod yazmadan düşünün. Serileştirme bu amaç elde etmek için kullanışlı bir mekanizma sağlar.

Ortak dil çalışma zamanı, nesnelerin bellekte nasıl depolandığını yönetir ve [yansıma](../../framework/reflection-and-codedom/reflection.md)kullanarak otomatikleştirilmiş bir serileştirme mekanizması sağlar. Bir nesne seri olduğunda, sınıf, derleme ve tüm veri üyeleri sınıf örneği adı için depolama yazılır. Üye değişkenleri genellikle depolama başvurularının diğer örnekleri nesneleri. Sınıf serileştirildiğinde, serileştirme altyapısı, aynı nesnenin birden çok kez serileştirilmemesini sağlamak için başvurulan nesneleri izler, zaten serileştirilir. .NET Framework ile birlikte sunulan serileştirme mimarisi, nesne grafiklerini ve döngüsel başvuruları otomatik olarak işler. Nesne grafiklerine uygulanan tek gereksinim, serileştirilmiş nesne tarafından başvurulan tüm nesnelerin aynı zamanda `Serializable` (daha fazla bilgi için bkz. [temel serileştirme](basic-serialization.md)) de işaretlenmiş olması olabilir. Bu yapılmadığı, işaretsiz nesneyi serileştirmek seri hale getirici girişiminde bulunduğunda bir özel durum.

Serileştirilmiş sınıf seri durumdan çıkarılmışsa, sınıf yeniden oluşturulur ve tüm veri üyelerinin değerleri otomatik olarak geri yüklenir.

## <a name="marshal-by-value"></a>Değere göre sıralama
Nesneleri oluşturulan burada yalnızca uygulama etki alanında geçerli değil. Nesneyi parametre olarak geçirme veya bir sonuç olarak döndürme girişimi, nesne öğesinden türetilmediği veya olarak işaretli olmadığı sürece başarısız olur `MarshalByRefObject` `Serializable` . Nesne olarak işaretlenmişse, `Serializable` nesne otomatik olarak serileştirilir, bir uygulama etki alanından diğerine taşınır ve sonra ikinci uygulama etki alanında nesnenin tam bir kopyasını oluşturmak için serisi kaldırılır. Bu işlem genellikle hazırlanır tarafından değeri olarak adlandırılır.

Bir nesne öğesinden `MarshalByRefObject` türetilirse, nesne başvurusu nesnenin kendisi yerine bir uygulama etki alanından diğerine geçirilir. Ayrıca, ' den türetilen bir nesneyi de işaretleyebilirsiniz `MarshalByRefObject` `Serializable` . Bu nesne uzaktan iletişim ile kullanıldığında, serileştirme işleminden sorumlu olan ve bir yedek seçiciyle () önceden yapılandırılmış olan biçimlendirici, `SurrogateSelector` serileştirme işleminin denetimini alır ve `MarshalByRefObject` bir ara sunucu ile türetilmiş tüm nesneleri değiştirir. Yerine, `SurrogateSelector` serileştirme mimarisi, [serileştirme işlemindeki adımlarda](steps-in-the-serialization-process.md)açıklanan standart serileştirme kurallarını izler.  

## <a name="related-sections"></a>İlgili bölümler  
 [İkili serileştirme](binary-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği ikili serileştirme mekanizması açıklanmaktadır.  
  
 [.NET uzaktan Iletişim](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
 Çeşitli iletişimleri .NET Framework için kullanılabilecek yöntemleri Uzaktan iletişimler açıklar.  
  
 [XML ve SOAP serileştirme](xml-and-soap-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği XML ve SOAP serileştirme mekanizması açıklanmaktadır.
