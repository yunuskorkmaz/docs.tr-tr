---
title: Derlemeler ve Genel Derleme Önbelleği (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
ms.openlocfilehash: 413d3266546fa1d2b403509793c62e76bca5bc70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717265"
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>Derlemeler ve Genel Derleme Önbelleği (Visual Basic)
Derlemeler dağıtım, sürüm denetimi, yeniden kullanma, aktivasyon kapsamı ve güvenlik izinleri için temel birimini oluşturur bir. AĞ tabanlı bir uygulama. Derlemeler, bir yürütülebilir (.exe) dosya veya dinamik bağlantı kitaplığı (.dll) dosyası biçiminde ve .NET Framework'ün yapı taşlarıdır. Bunlar, ortak dil çalışma zamanı tür uygulamalarına dikkat etmeniz gereken bilgileri sağlar. Derleme türleri ve mantıksal bir işlevsellik birimi oluşturacak ve birlikte çalışmak üzere tasarlanan kaynakları koleksiyonu olarak düşünebilirsiniz.  
  
 Derlemeler, bir veya daha fazla modül içerebilir. Örneğin, daha büyük projeleri birden fazla bireysel geliştiriciler ayrı modüllerde, tek bir derleme oluşturmak için bir araya tüm gelecek iş şekilde planlı. Modüller hakkında daha fazla bilgi için Ek Yardım konusuna [nasıl yapılır: Bir çoklu dosya derlemesi oluşturmak](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Derlemeleri, aşağıdaki özelliklere sahiptir:  
  
-   Derlemeleri, .exe veya .dll dosyaları olarak uygulanır.  
  
-   Bir derlemeyi genel derleme önbelleğinde koyarak uygulamalar arasında paylaşabilirsiniz. Derlemeleri güçlü-genel derleme önbelleğinde bulunan önce adlandırılması gerekir. Daha fazla bilgi için [Strong-Named derlemeleri](../../../../framework/app-domains/strong-named-assemblies.md).  
  
-   Derlemeleri, yalnızca gerekli olduğunda belleğe yüklenir. Kullanılmazlar, bunlar yüklü değildir. Başka bir deyişle, derlemeleri daha büyük projeler kaynakları yönetmek için etkili bir yol olabilir.  
  
-   Yansıma kullanarak program aracılığıyla bir derlemeyle ilgili bilgiler elde edebilirsiniz. Daha fazla bilgi için [yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Yalnızca incelemek için bir derlemeyi yüklemek istiyorsanız, bir yöntem gibi kullanın <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Derleme Bildirimi  
 Her derleme içinde bir *derleme bildirimi*. Benzer şekilde bir içindekiler tablosu, derleme bildirimi aşağıdakileri içerir:  
  
-   Derlemenin kimliğini (adı ve sürümü).  
  
-   Diğer tüm derlemeyi oluşturan, örneğin, .exe veya .dll dosyası, dayandığını oluşturduğunuz herhangi bir derleme dosyaların veya hatta bit eşlem ya da Benioku dosyaları tanımlayan bir dosya tablosu.  
  
-   Bir *derleme başvurusu listesi*, tüm dış bağımlılıkları listesi verilmiştir: .dll veya diğer dosyaları uygulama gereksinimlerinizi başkası tarafından oluşturulmuş olabilir. Derleme başvuruları, genel ve özel nesnelere başvurular içerir. Genel nesneler, genel derleme önbelleğinde biraz System32 dizininde gibi diğer uygulamalar tarafından kullanılabilir alanı bulunur. <xref:Microsoft.VisualBasic?displayProperty=nameWithType> Ad alanı genel derleme önbelleğindeki bir derleme bir örnektir. Özel nesneleri aynı düzeyde olarak veya uygulamanızı yüklendiği dizinin altında ya da bir dizin olmalıdır.  
  
 Derlemeleri içeriği, sürümleri ve bağımlılıkları hakkında bilgi içerdiğinden, Visual Basic ile oluşturduğunuz uygulamaların düzgün çalışması için Windows kayıt defteri değerlerini güvenmeyin. Derlemeler .dll çakışmalarını azaltmak ve daha güvenilir ve kolay dağıtmak uygulamalarınızı. Çoğu durumda, yüklediğiniz bir. Hedef bilgisayarın dosyaları kopyalama powershell'inizi yazarak NET tabanlı uygulama.  
  
 Daha fazla bilgi için [derleme bildirimi](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Bir derlemeye bir başvuru ekleme  
 Bir derlemeyi kullanması için buna bir başvuru eklemeniz gerekir. Ardından, kullandığınız [Imports deyimi](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) için ad alanı kullanmak istediğiniz öğeleri seçin. Bir derlemeye başvuru ve içeri aktarıldıktan sonra tüm erişilebilir sınıfları, özellikleri, yöntemleri ve diğer üyeleri, ad alanları kodlarını kaynak dosyanıza bir parçası değilmiş gibi uygulamanızda kullanılabilir.  
  
## <a name="creating-an-assembly"></a>Bir derleme oluşturma  
 Komut satırı derleyicisini kullanarak komut satırından oluşturarak uygulamanızı derleyin. Komut satırı derlemeleri oluşturma hakkında daha fazla ayrıntı için bkz [komut satırından derleme](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  Visual Studio'da bir derlemeyi derlemek için **derleme** menüsünde **yapı**.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Arkadaş derlemeler (Visual Basic)](friend-assemblies.md)
- [Nasıl yapılır: Bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma](how-to-share-an-assembly-with-other-applications.md)
- [Nasıl yapılır: Yük derlemeleri ve yüklemelerini kaldırma (Visual Basic)](how-to-load-and-unload-assemblies.md)
- [Nasıl yapılır: Bir dosyanın bir derleme (Visual Basic) olup olmadığını belirleme](how-to-determine-if-a-file-is-an-assembly.md)
- [Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma](how-to-create-and-use-assemblies-using-the-command-line.md)
- [İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [İzlenecek yol: Visual Studio'da (Visual Basic) Microsoft Office derlemelerinden tür bilgilerini katıştırma](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
