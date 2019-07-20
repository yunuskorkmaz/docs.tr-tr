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
ms.openlocfilehash: 8b2e14a7508d4a5e8069a3b98dee38a0ac62750c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363988"
---
# <a name="qualifying-net-types-for-interoperation"></a>Birlikte Çalışma için Niteleyici .NET Türleri
Türleri bir derlemede COM uygulamalarına sunmak istiyorsanız, tasarım zamanında COM birlikte çalışma gereksinimlerini göz önünde bulundurun. Yönetilen türler (sınıf, arabirim, yapı ve numaralandırma) aşağıdaki yönergelere uydığınızda COM türleriyle sorunsuz bir şekilde tümleşir:  
  
- Sınıfların arabirimleri açıkça uygulaması gerekir.  
  
     COM birlikte çalışabilirliği, sınıfın tüm üyelerini ve temel sınıfının üyelerini içeren bir arabirimi otomatik olarak oluşturmak için bir mekanizma sağlar, ancak açık arabirimler sağlamak çok daha iyidir. Otomatik olarak oluşturulan arabirime sınıf arabirimi denir. Yönergeler için bkz. [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Visual Basic, C#ve C++ ' yi kullanarak, kodunuzda ARABIRIM tanımlarını ekleyebilirsiniz (IDL) veya eşdeğerini kullanmak yerine. Sözdizimi ayrıntıları için dil belgelerinize bakın.  
  
- Yönetilen türler ortak olmalıdır.  
  
     Yalnızca bir derlemedeki ortak türler kaydedilir ve tür kitaplığına verilir. Sonuç olarak, yalnızca ortak türler COM tarafından görülebilir.  
  
     Yönetilen türler, COM 'a sunulmayan diğer yönetilen koda özellikler sunar. Örneğin, parametreli oluşturucular, statik yöntemler ve sabit alanlar COM istemcilerine gösterilmez. Diğer bir deyişle, çalışma zamanı bir tür içinde ve dışında veri sıraladığında, veriler kopyalanabilir veya dönüştürülebilirler.  
  
- Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır.  
  
     Ortak türlerin üyeleri COM 'a görünür olmaları durumunda da genel olmalıdır. Bir derlemenin görünürlüğünü, ortak bir türü veya genel bir türün genel üyelerini ' a uygulayarak <xref:System.Runtime.InteropServices.ComVisibleAttribute>kısıtlayabilirsiniz. Varsayılan olarak, tüm genel türler ve Üyeler görünür durumdadır.  
  
- Türler COM 'dan etkinleştirilecek Ortak parametresiz bir oluşturucuya sahip olmalıdır.  
  
     Yönetilen, ortak türler COM tarafından görülebilir. Ancak, Ortak parametresiz bir Oluşturucu (bağımsız değişken içermeyen bir Oluşturucu) olmadan, COM istemcileri türü oluşturamaz. COM istemcileri, başka bir yöntemle etkinleştirildiyse türü kullanmaya devam edebilir.  
  
- Türler özet olamaz.  
  
     Ne COM istemcisi ne de .NET istemcisi soyut türler oluşturabilir.  
  
 COM 'a aktarıldığında, yönetilen bir türün devralma hiyerarşisi düzleştirilir. Sürüm oluşturma yönetilen ve yönetilmeyen ortamlar arasında da farklılık gösterir. COM 'a sunulan türler, diğer yönetilen türlerle aynı sürüm oluşturma özelliklerine sahip değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [.NET Framework Bileşenlerini COM'da Gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface)
- [Birlikte Çalışma Özniteliklerini Uygulama](../../../docs/framework/interop/applying-interop-attributes.md)
- [COM için Bütünleştirilmiş Kod Paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
