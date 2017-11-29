---
title: "Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 23a1d8c638b198c31d7c83aaf3f216b465f01453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme
Bir katı adlı derlemeyi genel derleme önbelleğine (GAC) yüklemenin iki yolu vardır:  
  
> [!IMPORTANT]
>  Yalnızca katı adlı derlemeler GAC içine yüklenebilir. Tanımlayıcı adlı bir derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
-   Kullanarak [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).  
  
     Bunu, Visual Studio 2012 ve Visual Studio 2013'te bir InstallShield Limited Edition Projesi oluşturarak yaparsınız.  
  
     Bu, genel derleme önbelleğine derlemeler eklemenin önerilen ve en yaygın yoludur. Yükleyici, genel derleme önbelleğindeki derlemelerin referans amaçlı sayımını ve başka yararları sağlar.  
  
-   Kullanarak [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
     Genel derleme önbelleğine katı adlı derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için Gacutil.exe'yi kullanabilirsiniz.  
  
    > [!NOTE]
    >  Gacutil.exe yalnızca geliştirme amaçlıdır ve genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanılmamalıdır.  
  
> [!NOTE]
>  .NET Framework önceki sürümlerde Shfusion.dll Windows kabuk uzantısı, dosya Gezgini'nde sürükleyerek derlemelerini yüklemek etkin. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll artık kullanılmıyor.  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>Genel Derleme Önbelleği aracını (Gacutil.exe) kullanmak için.  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     **Gacutil -i** \< *derleme adı*>  
  
     Bu komutta *derleme adı* genel derleme önbelleğinde yüklenecek derlemenin adıdır.  
  
 Aşağıdaki örnek, bir dosya adı ile bir derlemeyi yükler `hello.dll` genel derleme önbelleğine.  
  
```  
gacutil -i hello.dll  
```  
  
 Daha fazla bilgi için bkz: [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>Bir InstallShield Limited Edition Projesi'ni kullanmak için  
  
1.  Kurulum ve dağıtım paketi, çözümünüz için kısayol menüsünü açarak ve ardından seçme çözümünüze ekleyin **Ekle**, **yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusunda **yüklü** klasörünü seçin **diğer proje türleri**, **Kurulum ve dağıtım**, **InstallShield Limited Edition**ve projenizin bir ad verin. (İstenirse, indirin, yükleyin ve InstallShield etkinleştirin.)  
  
3.  Kurulum ve dağıtım projenizin genel yapılandırma proje Yardımcısı'nda kullanarak ya da gerçekleştirmek **Çözüm Gezgini**, veya alt adımlar numaralı adımlarını seçerek **Çözüm Gezgini**. GAC derlemeleri ekleyecekseniz yaptığınız gibi ayarlarınızı yapılandırın.  
  
4.  Bir derlemeyi GAC'ye ekleme işlemini başlatmak için tercih **dosyaları**, altında olduğu **uygulama verilerini belirtin** adımını **Çözüm Gezgini**.  
  
5.  İçinde **hedef bilgisayarın klasörleri** bölmesinde için kısayol menüsünü açın **hedef bilgisayar**ve ardından **önceden tanımlanmış klasörünü göster**, **[ GlobalAssemblyCache]**.  
  
6.  Çözümde yer alan ve genel derleme önbelleğine yüklemek istediğiniz bir derlemeyi içeren her bir proje için:  
  
    1.  İçinde **bilgisayarın klasörleri kaynak** bölmesinde projesini seçin.  
  
    2.  İçinde **hedef bilgisayarın klasörleri** bölmesinde seçin **[GlobalAssemblyCache]**.  
  
    3.  İçinde **bilgisayarın dosyalarını kaynağı** bölmesinde seçin **birincil çıktı** *< project_name >*.  
  
    4.  Adım c dosyasında sürükleyin **hedef bilgisayarın dosyaları** bölmesinde (veya **kopyalama** ve **Yapıştır** dosyanın kısayol menüsünden komutları).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlemeler ve genel derleme önbelleği ile çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Nasıl yapılır: bir derlemeyi genel derleme önbelleğinden kaldırma](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Nasıl yapılır: bir derlemeyi tanımlayıcı adla imzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Windows Installer dağıtımı](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
