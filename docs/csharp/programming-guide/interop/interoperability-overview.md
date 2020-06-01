---
title: Birlikte çalışabilirlik genel bakış-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 6546a379d6d851aafbced0931221dc19ca022a72
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241740"
---
# <a name="interoperability-overview-c-programming-guide"></a>Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)
Konu C# yönetilen kodu ve yönetilmeyen kod arasında birlikte çalışabilirliği etkinleştirme yöntemlerini açıklar.  
  
## <a name="platform-invoke"></a>Platform çağırma  
 *Platform çağırma* , yönetilen kodun, MICROSOFT Windows API 'dakiler gibi dinamik bağlantı kitaplıkları (dll 'ler) içinde uygulanan yönetilmeyen işlevleri çağırmasına olanak sağlayan bir hizmettir. İçe aktarılmış bir işlevi bulur ve çağırır ve bağımsız değişkenlerini (tamsayılar, dizeler, diziler, yapılar vb.) gerektiğinde birlikte çalışma sınırında sıralar.  
  
Daha fazla bilgi için bkz. [YÖNETILMEYEN DLL işlevlerini](../../../framework/interop/consuming-unmanaged-dll-functions.md) [kullanma ve bir wav dosyasını oynatmak için platform çağırma kullanma](./how-to-use-platform-invoke-to-play-a-wave-file.md).
  
> [!NOTE]
> [Ortak dil çalışma zamanı](../../../standard/clr.md) (CLR) sistem kaynaklarına erişimi yönetir. CLR dışındaki yönetilmeyen kodu çağırmak bu güvenlik mekanizmasını atlar ve bu nedenle bir güvenlik riski oluşturur. Örneğin, yönetilmeyen kod, CLR Güvenlik mekanizmalarını atlayarak doğrudan yönetilmeyen koddaki kaynakları çağırabilir. Daha fazla bilgi için bkz. [.net 'Teki güvenlik](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>C++ Birlikte Çalışma  
 C# veya başka bir .NET dilinde yazılmış kod tarafından tüketilebilmesi için yerel bir C++ sınıfını kaydırmak için de bilinen C++ birlikte çalışma (ıJW) seçeneğini kullanabilirsiniz. Bunu yapmak için, bir yerel DLL veya COM bileşeni kaydırmak üzere C++ kodu yazarsınız. Diğer .NET dillerinin aksine, Visual C++ yönetilen ve yönetilmeyen kodun aynı uygulamada ve hatta aynı dosyada yer almasını sağlayan birlikte çalışabilirlik desteğine sahiptir. Daha sonra, yönetilen bir derleme üretmek için **/clr** derleyici anahtarını kullanarak C++ kodunu derleyebilirsiniz. Son olarak, C# projenizde derlemeye bir başvuru ekler ve sarmalanmış nesneleri diğer yönetilen sınıfları kullandığınız gibi kullanırsınız.  
  
## <a name="exposing-com-components-to-c"></a>COM bileşenlerini C 'ye gösterme\#
 Bir C# projesinden bir COM bileşeni kullanabilirsiniz. Genel adımlar şu şekildedir:  
  
1. Kullanmak için bir COM bileşeni bulun ve kaydedin. Bir COM DLL kaydını kaydetmek veya kaydını silmek için Regsvr32. exe ' yi kullanın.  
  
2. Projeye COM bileşenine veya tür kitaplığına başvuru ekleyin.  
  
     Başvuruyu eklediğinizde, Visual Studio bir .NET birlikte çalışma derlemesini çıkarmak için giriş olarak bir tür kitaplığı alan [Tlbimp. exe (tür kitaplığı alma)](../../../framework/tools/tlbimp-exe-type-library-importer.md)kullanır. Ayrıca, çalışma zamanı çağrılabilir sarmalayıcı (RCW) adlı derleme, tür kitaplığındaki COM sınıflarını ve arabirimlerini sarmalayan yönetilen sınıfları ve arabirimleri içerir. Visual Studio, oluşturulan derleme için projeye bir başvuru ekler.  
  
3. RCW 'da tanımlanan bir sınıfın örneğini oluşturun. Bu, sırasıyla COM nesnesinin bir örneğini oluşturur.  
  
4. Nesneyi diğer yönetilen nesneleri kullandığınız şekilde kullanın. Nesne çöp toplama tarafından geri kazanılır, COM nesnesinin örneği de bellekten serbest bırakılır.  
  
 Daha fazla bilgi için bkz. [com bileşenlerini .NET Framework gösterme](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>C# ' den COM ' a gösterme  
 COM istemcileri, doğru bir şekilde kullanıma sunulan C# türlerini kullanabilir. C# türlerini sergilemek için temel adımlar şunlardır:  
  
1. C# projesine birlikte çalışma özniteliklerini ekleyin.  
  
     Visual C# proje özelliklerini değiştirerek bir derlemeyi COM görünebilir hale getirebilirsiniz. Daha fazla bilgi için bkz. [derleme bilgileri Iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Bir COM tür kitaplığı oluşturun ve bunu COM kullanımı için kaydedin.  
  
     Visual C# proje özelliklerini değiştirerek, COM birlikte çalışma için C# derlemesini otomatik olarak kaydedebilirsiniz. Visual Studio, bir tür kitaplığı oluşturmak için yönetilen bir derlemeyi giriş olarak alan komut satırı anahtarını kullanarak [Regasm. exe ' yi (derleme kayıt aracı)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)kullanır `/tlb` . Bu tür kitaplığı `public` derlemedeki türleri açıklar ve com istemcilerinin yönetilen sınıflar oluşturabilmesi için kayıt defteri girişleri ekler.  
  
 Daha fazla bilgi için bkz. COM ve [örnek com sınıfına](./example-com-class.md) [.NET Framework bileşenleri gösterme](../../../framework/interop/exposing-dotnet-components-to-com.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Birlikte çalışma performansını iyileştirme](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [COM ve .NET arasında birlikte çalışabilirliğe giriş](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Visual Basic COM birlikte çalışabilirliğine giriş](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Yönetilen ve yönetilmeyen kod arasında sıralama](../../../framework/interop/interop-marshaling.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
- [C# Programlama Kılavuzu](../index.md)
