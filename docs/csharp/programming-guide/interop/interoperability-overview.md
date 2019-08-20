---
title: Birlikte çalışabilirlik genel C# bakış-Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 0414166cb4d101b9f2654824b3c5ce4b9689deff
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588965"
---
# <a name="interoperability-overview-c-programming-guide"></a>Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)
Bu konu, yönetilen kod ve yönetilmeyen kod C# arasında birlikte çalışabilirliği etkinleştirme yöntemlerini açıklar.  
  
## <a name="platform-invoke"></a>Platform çağırma  
 *Platform çağırma* , yönetilen kodun, MICROSOFT Windows API 'dakiler gibi dinamik bağlantı kitaplıkları (dll 'ler) içinde uygulanan yönetilmeyen işlevleri çağırmasına olanak sağlayan bir hizmettir. İçe aktarılmış bir işlevi bulur ve çağırır ve bağımsız değişkenlerini (tamsayılar, dizeler, diziler, yapılar vb.) gerektiğinde birlikte çalışma sınırında sıralar.  
  
 Daha fazla bilgi için bkz. [yönetilmeyen DLL işlevlerini](../../../framework/interop/consuming-unmanaged-dll-functions.md) kullanma [ve nasıl yapılır: Bir Wave dosyasını](./how-to-use-platform-invoke-to-play-a-wave-file.md)oynatmak için platform çağırma 'yi kullanın.  
  
> [!NOTE]
>  [Ortak dil çalışma zamanı](../../../standard/clr.md) (CLR) sistem kaynaklarına erişimi yönetir. CLR dışındaki yönetilmeyen kodu çağırmak bu güvenlik mekanizmasını atlar ve bu nedenle bir güvenlik riski oluşturur. Örneğin, yönetilmeyen kod, CLR Güvenlik mekanizmalarını atlayarak doğrudan yönetilmeyen koddaki kaynakları çağırabilir. Daha fazla bilgi için bkz. [.net 'Teki güvenlik](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>C++ Birlikte Çalışma  
 Yerel bir sınıfı C++ , C++ C# ya da başka bir .NET Framework dilde yazılmış kodla tüketilebilmesi için, yerel bir sınıfı kaydırmak IÇIN de bilinen birlikte çalışma (IJW) seçeneğini kullanabilirsiniz. Bunu yapmak için, yerel bir C++ dll veya com bileşenini kaydırmak üzere kod yazarsınız. Diğer .NET Framework dillerinin aksine, Visual C++ , yönetilen ve yönetilmeyen kodun aynı uygulamada ve hatta aynı dosyada yer almasını sağlayan, birlikte çalışabilirlik desteğine sahiptir. Daha sonra, C++ bir yönetilen derleme üretmek için **/clr** derleyici anahtarını kullanarak kodu derleyebilirsiniz. Son olarak, C# projenizdeki derlemeye bir başvuru ekler ve sarmalanmış nesneleri diğer yönetilen sınıfları kullandığınız gibi kullanırsınız.  
  
## <a name="exposing-com-components-to-c"></a>COM bileşenlerini C 'ye gösterme\#
 Bir C# projeden com bileşeni kullanabilirsiniz. Genel adımlar aşağıdaki gibidir:  
  
1. Kullanmak için bir COM bileşeni bulun ve kaydedin. Bir COM DLL kaydını kaydetmek veya kaydını silmek için Regsvr32. exe ' yi kullanın.  
  
2. Projeye COM bileşenine veya tür kitaplığına başvuru ekleyin.  
  
     Başvuruyu eklediğinizde, Visual Studio bir .NET Framework birlikte çalışma derlemesini çıkarmak için giriş olarak bir tür kitaplığı alan [Tlbimp. exe (tür kitaplığı alma)](../../../framework/tools/tlbimp-exe-type-library-importer.md)kullanır. Ayrıca, çalışma zamanı çağrılabilir sarmalayıcı (RCW) adlı derleme, tür kitaplığındaki COM sınıflarını ve arabirimlerini sarmalayan yönetilen sınıfları ve arabirimleri içerir. Visual Studio, oluşturulan derleme için projeye bir başvuru ekler.  
  
3. RCW 'da tanımlanan bir sınıfın örneğini oluşturun. Bu, sırasıyla COM nesnesinin bir örneğini oluşturur.  
  
4. Nesneyi diğer yönetilen nesneleri kullandığınız şekilde kullanın. Nesne çöp toplama tarafından geri kazanılır, COM nesnesinin örneği de bellekten serbest bırakılır.  
  
 Daha fazla bilgi için bkz. [com bileşenlerini .NET Framework gösterme](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>COM C# 'a gösterme  
 COM istemcileri, doğru C# şekilde açığa çıkarılan türleri tüketebilir. Türleri açığa çıkarmak C# için temel adımlar şunlardır:  
  
1. C# Projeye birlikte çalışma özniteliklerini ekleyin.  
  
     Visual C# Project özelliklerini değiştirerek BIR derlemeyi com görünebilir hale getirebilirsiniz. Daha fazla bilgi için bkz. [derleme bilgileri Iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Bir COM tür kitaplığı oluşturun ve bunu COM kullanımı için kaydedin.  
  
     Visual C# Project özelliklerini DEĞIŞTIREREK, com birlikte çalışma için C# derlemeyi otomatik olarak kaydedebilirsiniz. Visual Studio, bir tür kitaplığı oluşturmak için yönetilen bir derlemeyi giriş olarak alan `/tlb` komut satırı anahtarını kullanarak [Regasm. exe ' yi (derleme kayıt aracı)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)kullanır. Bu tür kitaplığı derlemedeki `public` türleri açıklar ve com istemcilerinin yönetilen sınıflar oluşturabilmesi için kayıt defteri girişleri ekler.  
  
 Daha fazla bilgi için bkz. COM ve [örnek com sınıfına](./example-com-class.md) [.NET Framework bileşenleri gösterme](../../../framework/interop/exposing-dotnet-components-to-com.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Birlikte çalışma performansını iyileştirme](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [COM ve .NET arasında birlikte çalışabilirliğe giriş](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Visual Basic COM birlikte çalışabilirliğine giriş](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Yönetilen ve yönetilmeyen kod arasında sıralama](../../../framework/interop/interop-marshaling.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
- [C# Programlama Kılavuzu](../index.md)
