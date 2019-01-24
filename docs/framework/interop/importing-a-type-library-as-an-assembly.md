---
title: Tür Kitaplığını Derleme Olarak İçeri Aktarma
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e346b326255ea46babc2e4c9101a1724671514d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517580"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Tür Kitaplığını Derleme Olarak İçeri Aktarma
COM tür tanımları, genellikle bir tür kitaplığı içinde yer alır. Buna karşılık, CLS uyumlu derleyiciler türü meta verileri bir derleme oluşturur. İki tür bilgi kaynakları oldukça farklıdır. Bu konu, bir tür kitaplığından meta verileri oluşturma teknikleri açıklar. Elde edilen derlemeyi birlikte çalışma derlemesi adı verilir ve içerdiği tür bilgilerini COM türlerini kullanmak .NET Framework uygulamaları etkinleştirir.  
  
 Bu tür bilgiler, uygulamanızın kullanılabilir hale getirmek için iki yolu vardır:  
  
-   Tasarım-zamanı-yalnızca birlikte çalışma derlemelerini kullanarak: İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], derleyicinin tür bilgilerini birlikte çalışma bütünleştirilmiş kod yürütülebilir dosyanın içine gömmek için bildirebilirsiniz. Derleyici, uygulamanızın kullandığı tür bilgilerini katıştırır. Uygulamanızla birlikte çalışma derlemesi dağıtmak gerekmez. Önerilen yöntem budur.  
  
-   Birlikte çalışma derlemelerini dağıtma: Standart bir birlikte çalışma derlemesine başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesi uygulamanızla dağıtılması gerekir. Bu tekniği kullanır ve özel bir COM bileşeni kullanmıyorsanız, her zaman, yönetilen kodda birleştirmek istiyorsanız COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesi (PIA) başvuru. Üretme ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemelerini](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Tasarım-zamanı-yalnızca birlikte çalışma derlemelerini kullandığınızda, tür bilgilerini COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesine gömebilirsiniz. Ancak, birincil birlikte çalışma derlemesi uygulamanızla birlikte dağıtmak gerekmez.  
  
 Çoğu uygulama, bir COM bileşeni'nin tüm özelliklerini kullanmayın çünkü tasarım-zamanı-yalnızca birlikte çalışma bütünleştirilmiş kodlarını kullanarak, uygulamanızın boyutunu azaltır. Tür bilgilerini katıştırır, derleyici çok verimli olmasıdır; Uygulamanızı yalnızca birkaç yöntemi bir COM arabirimi üzerinde kullanıyorsa, derleyici kullanılmayan metotlar katıştırmak değil. Gömülü tür bilgileri içeren bir uygulama gibi başka bir uygulamayla etkileşimiyle ya da bir birincil birlikte çalışma derlemesi kullanan bir uygulama ile etkileşim kurar, ortak dil çalışma zamanı kullanan iki ile türleri olup olmadığını belirlemek için denklik kuralları yazın. aynı adı aynı COM türü temsil eder. Bu kurallar, COM nesnelerini kullanmak için bilmeniz gerekmez. Ancak, kurallarda ilgileniyorsanız bkz [tür Eşdeğerliği ve katıştırılmış birlikte çalışma türleri](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).  
  
## <a name="generating-metadata"></a>Meta verileri oluşturuluyor  
 COM tür kitaplıkları Loanlib.tlb gibi .tlb uzantılı sahip tek başına dosyalar olabilir. Bazı tür kitaplıklarının bir .dll veya .exe dosyasının kaynak bölümüne katıştırılır. Tür kitaplığı bilgisi diğer kaynakları .olb ve .ocx dosyalarıdır.  
  
 COM türü hedef uyarlamasını içeren tür kitaplığını bulduktan sonra türü meta verileri içeren bir birlikte çalışma derlemesi oluşturmak için aşağıdaki seçenekleriniz vardır:  
  
-   Visual Studio  
  
     Visual Studio COM türleri bir tür kitaplığındaki bir derleme meta verileri otomatik olarak dönüştürür. Yönergeler için [nasıl yapılır: Tür kitaplıklarına başvurular ekleme](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md) ve [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)).  
  
-   [Tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     Tür kitaplığı içeri Aktarıcı meta verileri elde edilen birlikte çalışma dosyasındaki ayarlamak için komut satırı seçenekleri sağlar, türleri, varolan bir tür kitaplığından içeri aktarır ve birlikte çalışma derlemesi ve bir ad alanı oluşturur. Yönergeler için [nasıl yapılır: Tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
-   <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> Sınıfı  
  
     Bu sınıfı coclass'ları ve arabirimler tür kitaplığında bir derleme içindeki meta verileri dönüştürmek için yöntemler sağlar. Bu, Tlbimp.exe aynı meta veri çıkışı üretir. Ancak, Tlbimp.exe, aksine <xref:System.Runtime.InteropServices.TypeLibConverter> sınıfı bir bellek içi tür kitaplığı için meta verileri dönüştürebilir.  
  
-   Özel sarmalayıcılar  
  
     Bir tür kitaplığı yok veya yanlış olduğunda, bir seçenek sınıfı veya arabirim tanımı yinelenen yönetilen kaynak kodunda oluşturmaktır. Ardından kaynak kodunu bir derleme meta verileri oluşturmak için çalışma zamanını hedefleyen bir derleyici ile derleme.  
  
     COM türleri manuel olarak tanımlamak için aşağıdaki öğeler erişiminiz olmalıdır:  
  
    -   Tanımlanan arabirimleri ve coclass'ları kesin açıklamaları.  
  
    -   Bir derleyici gibi C# uygun .NET Framework sınıf tanımları oluşturabilen derleyici.  
  
    -   Tür kitaplığını derlemeye dönüştürme kurallarını bilgi.  
  
     Özel bir sarmalayıcı yazma Gelişmiş bir tekniktir. Özel bir sarmalayıcı oluşturmak hakkında ek bilgi için bkz. [standart sarmalayıcıları özelleştirme](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100)).  
  
 COM birlikte çalışma içeri aktarma işlemi hakkında daha fazla bilgi için bkz: [tür kitaplığını derlemeye dönüştürme özeti](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [COM Bileşenlerini .NET Framework'te Gösterme](../../../docs/framework/interop/exposing-com-components.md)
- [Tür kitaplığını derlemeye dönüştürme özeti](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)
- [Standart sarmalayıcıları özelleştirme](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))
- [Yönetilen kodda COM türlerini kullanma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))
- [Birlikte Çalışma Projesi Derleme](../../../docs/framework/interop/compiling-an-interop-project.md)
- [Birlikte Çalışma Uygulamasını Dağıtma](../../../docs/framework/interop/deploying-an-interop-application.md)
- [Nasıl yapılır: Tür kitaplıklarına başvurular ekleme](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)
- [Nasıl yapılır: Tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)
- [İzlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
