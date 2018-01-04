---
title: "Derlemeler ve Genel Derleme Önbelleği (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 893d869b1abaf9caa6f4705f40750912081d7df2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>Derlemeler ve Genel Derleme Önbelleği (Visual Basic)
Derlemeleri form temel birimi dağıtım, sürüm denetimi, yeniden, etkinleştirme kapsamı ve güvenlik izinleri olan bir. NET tabanlı bir uygulama. Derlemeler bir yürütülebilir dosya (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyası şeklinde ve .NET Framework'ün yapı taşlarıdır. Ortak dil çalışma zamanı tür uygulamaları haberdar olmanız gereken bilgilerle sağlarlar. Derleme türleri ve işlevlerin bir mantıksal birim oluşturur ve birlikte çalışacak biçimde oluşturulmuş kaynak koleksiyonu olarak düşünebilirsiniz.  
  
 Derlemeler, bir veya daha fazla modül içerebilir. Örneğin, daha büyük projeler birkaç her bir geliştirici ayrı modülleri, birlikte tek bir derleme oluşturmak için tüm gelecek iş şekilde planlanan. Modüller hakkında daha fazla bilgi için Ek Yardım konusuna [nasıl yapılır: bir Multifile derleme](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Derlemeler, aşağıdaki özelliklere sahiptir:  
  
-   Derlemeleri .exe veya .dll dosyaları olarak uygulanır.  
  
-   Bir derlemeyi genel derleme önbelleğinde koyarak uygulamalar arasında paylaşabilirsiniz. Derlemeleri güçlü-genel derleme önbelleğinde dahil önce adlandırılması gerekir. Daha fazla bilgi için bkz: [Strong-Named derlemeler](../../../../framework/app-domains/strong-named-assemblies.md).  
  
-   Derlemeler, yalnızca gerekli olduğunda belleğe yüklenir. Bunlar kullanılmazsa, bunlar yüklü değildir. Başka bir deyişle, derlemeler daha büyük projeler alanındaki kaynakları yönetmek için etkili bir yol olabilir.  
  
-   Yansıma kullanarak program aracılığıyla bir derleme hakkında bilgi edinebilirsiniz. Daha fazla bilgi için bkz: [yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Yalnızca incelemek için bir derlemeyi yüklemek istiyorsanız, bir yöntem gibi kullanın <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Derleme Bildirimi  
 Her derleme bir *derleme bildirimi*. Benzer şekilde bir içindekiler tablosu, derleme bildirimi aşağıdakileri içerir:  
  
-   Derlemenin kimliği (adı ve sürüm).  
  
-   Tüm diğer derleme, örneğin, .exe veya .dll dosyasını, bağımlı oluşturulan diğer derlemeleri dosyaları veya hatta bit eşlem veya Benioku dosyaları açıklayan bir dosya tablosu.  
  
-   Bir *derleme başvurusu listesi*, tüm dış bağımlılıkları listesi olduğu — .dll veya diğer dosyaları uygulama gereksinimlerinizi başka birisi tarafından oluşturulmuş olabilir. Derleme başvurularını hem genel hem de özel nesnelere başvurular içerir. Genel derleme önbelleğinde biraz System32 dizini gibi diğer uygulamalar için kullanılabilir bir alan genel nesneler bulunur. <xref:Microsoft.VisualBasic?displayProperty=nameWithType> Ad alanı bir derlemeyi genel derleme önbelleğinde örneğidir. Özel nesneleri aynı düzeyde olarak veya uygulamanızın yüklendiği dizinin altında ya da bir dizin olmalıdır.  
  
 Derlemeleri içerik, sürüm ve bağımlılıklar hakkındaki bilgileri içerdiğinden, Visual Basic ile oluşturduğunuz uygulamaların düzgün çalışması için Windows kayıt defteri değerlerini kullanmayın. Derlemeler .dll çakışmaları azaltmak ve uygulamalarınızı daha güvenilir ve kolay dağıtmak yapın. Çoğu durumda, yüklediğiniz bir. Yalnızca kopyalayarak dosyalarından hedef bilgisayara NET tabanlı uygulama.  
  
 Daha fazla bilgi için bkz: [derleme bildirimi](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Bir derleme başvurusu ekleme  
 Bir derlemeyi kullanmak için bir başvuru eklemeniz gerekir. Ardından, kullandığınız [Imports deyimi](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ad alanını kullanmak istediğiniz öğeleri seçin. Bir derlemeyi başvurulan ve içe sonra erişilebilir tüm sınıfları, özellikleri, yöntemleri ve diğer üyelerin kendi ad alanları, kendi kodlarını kaynak dosyanızın parçası değilmiş gibi uygulamanız için kullanılabilir.  
  
## <a name="creating-an-assembly"></a>Derleme oluşturma  
 Komut satırı derleyicisini kullanarak komut satırından oluşturarak uygulamanızı derleyin. Komut satırından derlemeleri oluşturma hakkında daha fazla bilgi için bkz [komut satırından derleme](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  Visual Studio'da bir derleme üzerinde oluşturmak için **yapı** menüsünü seçin **yapı**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Arkadaş derlemeler (Visual Basic)](friend-assemblies.md)  
 [Nasıl yapılır: bir derlemeyi başka uygulamalarla (Visual Basic) paylaşma](how-to-share-an-assembly-with-other-applications.md)  
 [Nasıl yapılır: yükleme ve kaldırma derlemeler (Visual Basic)](how-to-load-and-unload-assemblies.md)  
 [Nasıl yapılır: bir dosyanın derleme (Visual Basic) olup olmadığını belirleme](how-to-determine-if-a-file-is-an-assembly.md)  
 [Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [İzlenecek yol: Visual Studio'da (Visual Basic) Microsoft Office derlemelerinden tür bilgilerini katıştırma](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
