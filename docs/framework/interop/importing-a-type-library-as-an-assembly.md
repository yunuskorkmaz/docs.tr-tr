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
ms.openlocfilehash: 89479ca4a41f761d4aacaf6d8d962bfba62be811
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="importing-a-type-library-as-an-assembly"></a>Tür Kitaplığını Derleme Olarak İçeri Aktarma
COM tür tanımları genellikle bir tür kitaplığı'nda bulunur. Buna karşılık, CLS uyumlu derleyicileri derlemedeki türü meta veriler üretir. İki kaynak türü bilgilerinin oldukça farklıdır. Bu konu, bir tür kitaplığından meta veri oluşturma teknikleri açıklar. Elde edilen derlemeyi birlikte çalışma derleme adı verilir ve COM türlerini kullanmak .NET Framework uygulamaları içerdiği türü bilgileri sağlar.  
  
 Bu tür bilgiler, uygulamanızın kullanılabilir hale getirmek için iki yolu vardır:  
  
-   Tasarım zamanı-yalnızca birlikte çalışma derlemeleri kullanma: itibaren [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yürütülebilir dosyanın birlikte çalışma derlemeye tür bilgilerini katıştırma görevlendirin. Derleyici, uygulamanızın kullandığı türü bilgilerini katıştırır. Uygulamanız ile birlikte çalışma derlemeyi dağıtmanız gerekmez. Önerilen yöntem budur.  
  
-   Birlikte çalışma derlemeleri dağıtma: birlikte çalışma derlemesi için standart bir başvuru oluşturabilirsiniz. Bu durumda, uygulamanız ile birlikte çalışma derlemesi dağıtılmalıdır. Bu yöntem uygulamadığınız ve özel bir COM bileşeni kullanmıyorsanız, her zaman yönetilen kodunuzda birleştirmek istiyorsanız COM bileşeni yazarı tarafından yayımlanan birincil birlikte çalışma derlemesi (PIA) başvuru. Oluşturan ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz: [birincil birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Tasarım zamanı-yalnızca birlikte çalışma derlemeleri kullandığınızda, COM bileşeninin yazar tarafından yayımlanan birincil birlikte çalışma derlemesi tür bilgilerini katıştırma. Ancak, uygulamanız ile birincil birlikte çalışma derlemesi dağıtmak gerekmez.  
  
 Çoğu uygulamayı bir COM bileşeni'nin tüm özelliklerini kullanmadığından tasarım-zamanı-yalnızca birlikte çalışma derlemeleri kullanarak, uygulamanızın boyutunu azaltır. Tür bilgilerini katıştırır yüklediğinizde derleyici çok verimli olur; Uygulamanız yalnızca bazı yöntemlere bir COM arabirimi kullanıyorsa derleyici kullanılmayan yöntemleri katıştırmak değil. Katıştırılmış türde bilgi içeren bir uygulama gibi başka bir uygulama ile etkileşim veya birincil birlikte çalışma derlemesi kullanan bir uygulama ile etkileşime giren, ortak dil çalışma zamanı kullandığı iki ile türleri olup olmadığını belirlemek için eşdeğer kuralları yazın. aynı adı aynı COM türünü temsil eder. COM nesneleri kullanmak için bu kurallar bilmek zorunda değildir. Ancak, kurallarda ilgileniyorsanız, bkz [tür Eşdeğerliği ve katıştırılmış birlikte çalışma türlerini](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).  
  
## <a name="generating-metadata"></a>Meta veri oluşturma  
 COM tür kitaplıklarının Loanlib.tlb gibi bir .tlb uzantısına sahip tek başına dosya olabilir. Bazı tür kitaplıklarının bir .dll veya .exe dosyasının kaynak bölümüne katıştırılır. Diğer bilgi kaynaklarıyla ilgili tür kitaplığı .olb ve .ocx dosyalarıdır.  
  
 COM türü hedef uygulaması içeren tür kitaplığı bulduktan sonra türü meta verileri içeren bir birlikte çalışma derleme oluşturmak için aşağıdaki seçenekleriniz vardır:  
  
-   Visual Studio  
  
     Visual Studio derleme meta verilerini otomatik olarak bir tür kitaplığı COM türlerinde dönüştürür. Yönergeler için bkz: [nasıl yapılır: tür kitaplıklarına Başvuru Ekle](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md) ve [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)).  
  
-   [Tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     Tür kitaplığı içeri Aktarıcı meta verileri elde edilen birlikte çalışma dosyasındaki ayarlamak için komut satırı seçenekleri sağlar, türleri var olan bir tür kitaplığından içeri aktarır ve birlikte çalışabilirlik bütünleştirilmiş kod ve bir ad alanı oluşturur. Yönergeler için bkz: [nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturmak](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
-   <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> sınıfı  
  
     Bu sınıf coclass'ları ve bir tür kitaplığı arabirimlerde derlemedeki meta verileri dönüştürmek için yöntemleri sağlar. Tlbimp.exe aynı meta veri çıkışı üretir. Ancak, Tlbimp.exe, aksine <xref:System.Runtime.InteropServices.TypeLibConverter> sınıfı, bir bellek içi tür kitaplığı meta verileri dönüştürebilir.  
  
-   Özel sarmalayıcılar  
  
     Bir tür kitaplığı kullanılamıyor ya da yanlış olduğunda, bir seçenek sınıfı veya arabirimi yinelenen tanımının yönetilen kaynak kodunda oluşturmaktır. Ardından, derlemedeki meta verileri üretmek için çalışma zamanı hedefleyen bir derleme kaynak koduyla de derleyin.  
  
     COM türlerini manuel olarak tanımlamak için aşağıdaki öğeleri erişiminiz olmalıdır:  
  
    -   Kesin açıklamaları tanımlanmakta arabirimleri ve coclass'ları.  
  
    -   Uygun .NET Framework sınıf tanımları oluşturabilen C# Derleyici gibi bir derleyici.  
  
    -   Tür kitaplığını derleme dönüştürme kurallarını bilgi.  
  
     Özel bir sarmalayıcı yazma Gelişmiş bir tekniktir. Özel bir sarmalayıcı oluşturur hakkında ek bilgi için bkz: [özelleştirme standart sarmalayıcıları](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100)).  
  
 COM birlikte çalışma alma işlemi hakkında daha fazla bilgi için bkz: [derleme dönüştürme özeti için tür kitaplığı](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 [COM Bileşenlerini .NET Framework'te Gösterme](../../../docs/framework/interop/exposing-com-components.md)  
 [Derleme dönüştürme özeti için tür kitaplığı](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Standart sarmalayıcıları özelleştirme](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))  
 [Yönetilen kodda COM türlerini kullanma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
 [Birlikte Çalışma Projesi Derleme](../../../docs/framework/interop/compiling-an-interop-project.md)  
 [Birlikte Çalışma Uygulamasını Dağıtma](../../../docs/framework/interop/deploying-an-interop-application.md)  
 [Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)  
 [Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Bütünleştirilmiş Kodları Oluşturma](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)  
 [İzlenecek yol: Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
