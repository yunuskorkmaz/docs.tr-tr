---
title: Birlikte Çalışma için Niteleyici .NET Türleri
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cad67f52a4ca977606d7b5a307868ff129570e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032664"
---
# <a name="qualifying-net-types-for-interoperation"></a>Birlikte Çalışma için Niteleyici .NET Türleri
COM uygulamaları için bir bütünleştirilmiş kodundaki türler kullanıma sunmak istiyorsanız, tasarım zamanında COM birlikte çalışabilirlik gereksinimlerini göz önünde bulundurun. Aşağıdaki yönergelere uyunuz, yönetilen türler (sınıfı, arabirim, yapı ve sabit listesi) COM türleri ile sorunsuz şekilde tümleştirin:  
  
- Sınıfları, arabirimleri açıkça uygulamalıdır.  
  
     COM birlikte çalışma otomatik olarak bir sınıfın tüm üyeleri ve temel sınıfın üyelerini içeren bir arabirim oluşturmak için bir mekanizma sağlar, ancak açık bir arabirim sağlamak çok daha iyidir. Otomatik olarak oluşturulan arabirimi sınıf arabirimi çağrılır. Yönergeler için bkz: [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Visual Basic kullanabileceğiniz C#ve C++ arabirim tanımlama dili (IDL) ya da eşdeğerine kullanmak zorunda olmak yerine kodunuzun içinde Arabirim tanımları birleştirmek için. Söz dizimi ayrıntılarını dil belgelerinize bakın.  
  
- Yönetilen türler genel olmalıdır.  
  
     Yalnızca genel türleri bir derlemede kayıtlı ve için tür kitaplığı dışarı. Sonuç olarak, yalnızca genel türler COM'a görünebilir  
  
     Türleri sunmaya özellikleri COM'a gösterilmeyen diğer yönetilen kod için yönetilen Örneğin, parametreli Oluşturucular, statik yöntemleri ve sabit alanlarını COM istemcilerine sunulmaz. Çalışma zamanı türü veriyi sürekliliğe devreder gibi daha fazla veri dönüştürülür ve kopyalanmak.  
  
- Yöntemler, özellikler, alanlar ve olaylar, ortak olmalıdır.  
  
     Genel türlerin üyelerini de COM'a görünür olmasını olmaları durumunda ortak olmalıdır Uygulayarak bir derleme, ortak bir türü veya genel bir türün genel üyeleri görünürlüğünü kısıtlayabilirsiniz <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Varsayılan olarak, tüm genel türler ve üyeler görülebilir.  
  
- Türleri COM'dan etkinleştirilmesi için bir ortak varsayılan oluşturucusu olmalıdır  
  
     Yönetilen, genel türler COM'a görünebilir Ancak, bir ortak varsayılan Oluşturucusu (bağımsız değişken içermeyen bir oluşturucu) tür COM istemcileri oluşturulamıyor. Başka bir yolla tarafından etkinleştirilmişse COM istemcileri türü kullanmaya devam edebilirsiniz.  
  
- Türleri Özet olamaz.  
  
     Soyut türlerin COM istemcilerini ne .NET istemcileri oluşturabilirsiniz.  
  
 COM dışarı aktardığınızda, yönetilen bir tür devralma hiyerarşisinde düzleştirilir. Sürüm oluşturma, yönetilen ve yönetilmeyen ortamlar arasında da farklılık gösterir. Türler com'a diğer yönetilen türleri aynı sürüm özelliklere sahip değilsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [.NET Framework Bileşenlerini COM'da Gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface)
- [Birlikte Çalışma Özniteliklerini Uygulama](../../../docs/framework/interop/applying-interop-attributes.md)
- [COM için Bütünleştirilmiş Kod Paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
