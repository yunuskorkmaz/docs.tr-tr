---
title: COM birlikte çalışma için .NET türlerini nitelendirme
description: Bu makalede, bir .NET derlemesindeki türleri COM birlikte çalışabilirliğine yönelik COM uygulamalarına açığa çıkarmak için yönergeler sağlanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 5b122befffbcad39258393462c75ac20431d9136
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420506"
---
# <a name="qualifying-net-types-for-com-interoperation"></a>COM birlikte çalışma için .NET türlerini nitelendirme
Türleri bir derlemede COM uygulamalarına sunmak istiyorsanız, tasarım zamanında COM birlikte çalışma gereksinimlerini göz önünde bulundurun. Yönetilen türler (sınıf, arabirim, yapı ve numaralandırma) aşağıdaki yönergelere uydığınızda COM türleriyle sorunsuz bir şekilde tümleşir:  
  
- Sınıfların arabirimleri açıkça uygulaması gerekir.  
  
     COM birlikte çalışabilirliği, sınıfın tüm üyelerini ve temel sınıfının üyelerini içeren bir arabirimi otomatik olarak oluşturmak için bir mekanizma sağlar, ancak açık arabirimler sağlamak çok daha iyidir. Otomatik olarak oluşturulan arabirime sınıf arabirimi denir. Yönergeler için bkz. [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Visual Basic, C# ve C++ ' ı, arabirim tanımı dili (IDL) veya eşdeğerini kullanmak yerine kodunuzda arabirim tanımlarını eklemek için kullanabilirsiniz. Sözdizimi ayrıntıları için dil belgelerinize bakın.  
  
- Yönetilen türler ortak olmalıdır.  
  
     Yalnızca bir derlemedeki ortak türler kaydedilir ve tür kitaplığına verilir. Sonuç olarak, yalnızca ortak türler COM tarafından görülebilir.  
  
     Yönetilen türler, COM 'a sunulmayan diğer yönetilen koda özellikler sunar. Örneğin, parametreli oluşturucular, statik yöntemler ve sabit alanlar COM istemcilerine gösterilmez. Diğer bir deyişle, çalışma zamanı bir tür içinde ve dışında veri sıraladığında, veriler kopyalanabilir veya dönüştürülebilirler.  
  
- Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır.  
  
     Ortak türlerin üyeleri COM 'a görünür olmaları durumunda da genel olmalıdır. Bir derlemenin görünürlüğünü, ortak bir türü veya genel bir türün genel üyelerini ' a uygulayarak kısıtlayabilirsiniz <xref:System.Runtime.InteropServices.ComVisibleAttribute> . Varsayılan olarak, tüm genel türler ve Üyeler görünür durumdadır.  
  
- Türler COM 'dan etkinleştirilecek Ortak parametresiz bir oluşturucuya sahip olmalıdır.  
  
     Yönetilen, ortak türler COM tarafından görülebilir. Ancak, Ortak parametresiz bir Oluşturucu (bağımsız değişken içermeyen bir Oluşturucu) olmadan, COM istemcileri türü oluşturamaz. COM istemcileri, başka bir yöntemle etkinleştirildiyse türü kullanmaya devam edebilir.  
  
- Türler özet olamaz.  
  
     Ne COM istemcisi ne de .NET istemcisi soyut türler oluşturabilir.  
  
 COM 'a aktarıldığında, yönetilen bir türün devralma hiyerarşisi düzleştirilir. Sürüm oluşturma yönetilen ve yönetilmeyen ortamlar arasında da farklılık gösterir. COM 'a sunulan türler, diğer yönetilen türlerle aynı sürüm oluşturma özelliklerine sahip değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [.NET Framework Bileşenlerini COM'da Gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface)
- [Birlikte Çalışma Özniteliklerini Uygulama](../../../docs/standard/native-interop/apply-interop-attributes.md)
- [COM için bir .NET Framework derlemesi paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
