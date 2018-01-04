---
title: "Nasıl yapılır: COM Sarmalayıcıları Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646c7fc6a8ebbb68f210637086db0e968e3533c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-com-wrappers"></a>Nasıl yapılır: COM Sarmalayıcıları Oluşturma
Bileşen Nesne Modeli (COM) sarmalayıcıları kullanarak oluşturabileceğiniz [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] özellikleri veya .NET Framework Araçları Tlbimp.exe ve Regasm.exe. Her iki yöntem de iki tür COM sarmalayıcıları oluştur:  
  
-   A [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) yönetilen kodda bir COM nesnesi çalıştırmak için bir tür kitaplığı.  
  
-   A [COM aranabilir sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md) yönetilen bir nesnenin bir yerel uygulamayı çalıştırmak için gerekli kayıt defteri ayarları.  
  
 İçinde [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], projenizin bir başvuru olarak COM sarmalayıcı ekleyebilirsiniz.  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a>Yönetilen bir uygulamada COM nesneleri kaydırma  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için  
  
1.  Yönetilen uygulamanızın projeyi açın.  
  
2.  Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.  
  
3.  Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.  
  
4.  Başvuru Ekle iletişim kutusunda tıklatın **COM** sekmesinde, kullanın ve istediğiniz bileşeni seçin **Tamam**.  
  
     İçinde **Çözüm Gezgini**, COM bileşeni projenize başvuruları klasöre eklendiğine dikkat edin.  
  
 Şimdi COM nesnesi erişmek için kod yazabilirsiniz. Nesne gibi ile bildirerek başlamak için bir `Imports` deyimi için [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] veya `Using` bildirimi [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].  
  
> [!NOTE]
>  Program Microsoft Office bileşenleri istiyorsanız, önce yükleme [Microsoft Office birincil birlikte çalışma derlemeleri](http://go.microsoft.com/fwlink/?LinkId=50479) (PIA) Microsoft Download Center gelen. 4. adımda Nesne Kitaplığı istediğiniz gibi Office ürün için kullanılabilir en son sürümünü seçin **Microsoft Word 11.0 Nesne Kitaplığı**.  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>.NET Framework Araçları'nı kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için  
  
-   Çalıştırma [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) aracı.  
  
 Bu araç, özgün Tür Kitaplığı'nda tanımlanan türler için çalışma zamanı meta verileri içeren bütünleştirilmiş oluşturur.  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a>Yerel uygulama nesnelerinin kaydırma yönetilen  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak bir COM aranabilir sarmalayıcısı oluşturmak için  
  
1.  Yerel kodda çalıştırmak istediğiniz yönetilen sınıfı için sınıf kitaplığı projesi oluşturun. Sınıfı, varsayılan bir oluşturucu olması gerekir.  
  
     AssemblyInfo dosyası, derlemede için dört bölümden oluşan tam sürüm numarası sahip olduğunuzu doğrulayın. Bu numara, Windows kayıt defterinde sürüm bakımı için gereklidir. Sürüm numaraları hakkında daha fazla bilgi için bkz: [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2.  Üzerinde **proje** menüsünde tıklatın **özellikleri**.  
  
3.  Tıklatın **derleme** sekmesi.  
  
4.  Seçin **kaydetmek için COM birlikte çalışma** onay kutusu.  
  
 Projesi derlerken, derleme COM birlikte çalışma için otomatik olarak kaydedilir. Yerel bir uygulama geliştiriyorsanız [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], tıklatarak derleme kullanabilirsiniz **Başvuru Ekle** üzerinde **proje** menüsü.  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>.NET Framework Araçları'nı kullanarak bir COM aranabilir sarmalayıcısı oluşturmak için  
  
-   Çalıştırma [Regasm.exe (derleme kayıt aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) aracı.  
  
 Bu araç, derleme meta verilerini okur ve gerekli girişleri kayıt defterine ekler. Sonuç olarak, COM istemcileri, .NET Framework sınıfları şeffaf bir şekilde oluşturabilirsiniz. Yerel bir COM sınıfı değilmiş gibi derleme kullanabilirsiniz.  
  
 Herhangi bir dizinde bulunan bir derleme Regasm.exe çalışır ve ardından çalıştırın [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel derleme önbelleğine taşıyın. Derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir çünkü derleme taşıma konum kayıt defteri girdilerini geçersiz kılmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanında Çağrılabilir Sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [COM Çağrılabilir Sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md)
