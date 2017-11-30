---
title: "Derlemeler ve Genel Derleme Önbelleği (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3743c07f1de1d39f07d559aa161e4547422a6e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>Derlemeler ve Genel Derleme Önbelleği (C#)
Derlemeleri form temel birimi dağıtım, sürüm denetimi, yeniden, etkinleştirme kapsamı ve güvenlik izinleri olan bir. NET tabanlı bir uygulama. Derlemeler bir yürütülebilir dosya (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyası şeklinde ve .NET Framework'ün yapı taşlarıdır. Ortak dil çalışma zamanı tür uygulamaları haberdar olmanız gereken bilgilerle sağlarlar. Derleme türleri ve işlevlerin bir mantıksal birim oluşturur ve birlikte çalışacak biçimde oluşturulmuş kaynak koleksiyonu olarak düşünebilirsiniz.  
  
 Derlemeler, bir veya daha fazla modül içerebilir. Örneğin, daha büyük projeler birkaç her bir geliştirici ayrı modülleri, birlikte tek bir derleme oluşturmak için tüm gelecek iş şekilde planlanan. Modüller hakkında daha fazla bilgi için Ek Yardım konusuna [nasıl yapılır: bir Multifile derleme](https://msdn.microsoft.com/library/226t7yxe).  
  
 Derlemeler, aşağıdaki özelliklere sahiptir:  
  
-   Derlemeleri .exe veya .dll dosyaları olarak uygulanır.  
  
-   Bir derlemeyi genel derleme önbelleğinde koyarak uygulamalar arasında paylaşabilirsiniz. Derlemeleri güçlü-genel derleme önbelleğinde dahil önce adlandırılması gerekir. Daha fazla bilgi için bkz: [Strong-Named derlemeler](https://msdn.microsoft.com/library/wd40t7ad).  
  
-   Derlemeler, yalnızca gerekli olduğunda belleğe yüklenir. Bunlar kullanılmazsa, bunlar yüklü değildir. Başka bir deyişle, derlemeler daha büyük projeler alanındaki kaynakları yönetmek için etkili bir yol olabilir.  
  
-   Yansıma kullanarak program aracılığıyla bir derleme hakkında bilgi edinebilirsiniz. Daha fazla bilgi için bkz: [yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
-   Yalnızca incelemek için bir derlemeyi yüklemek istiyorsanız, bir yöntem gibi kullanın <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Derleme Bildirimi  
 Her derleme bir *derleme bildirimi*. Benzer şekilde bir içindekiler tablosu, derleme bildirimi aşağıdakileri içerir:  
  
-   Derlemenin kimliği (adı ve sürüm).  
  
-   Tüm diğer derleme, örneğin, .exe veya .dll dosyasını, bağımlı oluşturulan diğer derlemeleri dosyaları veya hatta bit eşlem veya Benioku dosyaları açıklayan bir dosya tablosu.  
  
-   Bir *derleme başvurusu listesi*, tüm dış bağımlılıkları listesi olduğu — .dll veya diğer dosyaları uygulama gereksinimlerinizi başka birisi tarafından oluşturulmuş olabilir. Derleme başvurularını hem genel hem de özel nesnelere başvurular içerir. Genel derleme önbelleğinde başka uygulamalar için kullanılabilir bir alan genel nesneler bulunur. Özel nesneleri aynı düzeyde olarak veya uygulamanızın yüklendiği dizinin altında ya da bir dizin olmalıdır.  
  
 Derlemeleri içerik, sürüm ve bağımlılıklar hakkındaki bilgileri içerdiğinden, C# ile oluşturduğunuz uygulamaların düzgün çalışması için Windows kayıt defteri değerlerini kullanmayın. Derlemeler .dll çakışmaları azaltmak ve uygulamalarınızı daha güvenilir ve kolay dağıtmak yapın. Çoğu durumda, yüklediğiniz bir. Yalnızca kopyalayarak dosyalarından hedef bilgisayara NET tabanlı uygulama.  
  
 Daha fazla bilgi için bkz: [derleme bildirimi](https://msdn.microsoft.com/library/1w45z383).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Bir derleme başvurusu ekleme  
 Bir derlemeyi kullanmak için bir başvuru eklemeniz gerekir. Ardından, kullandığınız [using yönergesi](../../../../csharp/language-reference/keywords/using-directive.md) ad alanını kullanmak istediğiniz öğeleri seçin. Bir derlemeyi başvurulan ve içe sonra erişilebilir tüm sınıfları, özellikleri, yöntemleri ve diğer üyelerin kendi ad alanları, kendi kodlarını kaynak dosyanızın parçası değilmiş gibi uygulamanız için kullanılabilir.  
  
 C# ' ta aynı derlemesinin iki sürümü de tek bir uygulama kullanabilirsiniz. Daha fazla bilgi için bkz: [extern alias](../../../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Derleme oluşturma  
 Tıklayarak uygulamanızı derleyin **yapı** üzerinde **yapı** menü veya komut satırı derleyicisini kullanarak komut satırından oluşturma. Komut satırından derlemeleri oluşturma hakkında daha fazla bilgi için bkz [komut satırı derleme ile csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
> [!NOTE]
>  Visual Studio'da bir derleme üzerinde oluşturmak için **yapı** menüsünü seçin **yapı**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Ortak dil çalışma zamanı derlemeleri](https://msdn.microsoft.com/library/k3677y81)  
 [Arkadaş derlemeler (C#)](friend-assemblies.md)  
 [Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma](how-to-share-an-assembly-with-other-applications.md)  
 [Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)](how-to-load-and-unload-assemblies.md)  
 [Nasıl yapılır: bir dosyanın derleme (C#) olup olmadığını belirleme](how-to-determine-if-a-file-is-an-assembly.md)  
 [Nasıl yapılır: komut satırını (C#) kullanarak derlemeler oluşturma ve kullanma](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [İzlenecek yol: Visual Studio'da (C#) Microsoft Office derlemelerinden tür bilgilerini katıştırma](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
