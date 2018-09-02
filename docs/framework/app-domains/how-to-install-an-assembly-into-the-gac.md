---
title: 'Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c3bd568cf504125bc99801815d08764417b42cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469004"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme
Bir katı adlı derlemeyi genel derleme önbelleğine (GAC) yüklemenin iki yolu vardır:  
  
> [!IMPORTANT]
>  Yalnızca katı adlı derlemeler GAC içine yüklenebilir. Bir katı adlı derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
-   Kullanarak [Windows Installer](/windows/desktop/Msi/windows-installer-portal).  
  
     Bunu, Visual Studio 2012 ve Visual Studio 2013'te bir InstallShield Limited Edition Projesi oluşturarak yaparsınız.  
  
     Bu, genel derleme önbelleğine derlemeler eklemenin önerilen ve en yaygın yoludur. Yükleyici, genel derleme önbelleğindeki derlemelerin referans amaçlı sayımını ve başka yararları sağlar.  
  
-   Kullanarak [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
     Genel derleme önbelleğine katı adlı derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için Gacutil.exe'yi kullanabilirsiniz.  
  
    > [!NOTE]
    >  Gacutil.exe yalnızca geliştirme amaçlıdır ve genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanılmamalıdır.  
  
> [!NOTE]
>  Önceki .NET Framework sürümlerinde, Shfusion.dll Windows kabuk uzantısı derlemeleri dosya Gezgini'nde sürükleyerek yüklemenize olanak etkin. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll kullanımdan kalkmıştır.  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>Genel Derleme Önbelleği aracını (Gacutil.exe) kullanmak için.  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     **Gacutil -i** \< *derleme adı*>  
  
     Bu komutta *derleme adı* genel bütünleştirilmiş kod önbelleğine yüklenecek derlemenin adıdır.  
  
 Aşağıdaki örnek, dosya adı ile bir derlemeyi yükler `hello.dll` genel bütünleştirilmiş kod önbelleğine.  
  
```  
gacutil -i hello.dll  
```  
  
 Daha fazla bilgi için [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>Bir InstallShield Limited Edition Projesi'ni kullanmak için  
  
1.  Çözümünüz için kısayol menüsünü açıp ardından çözümünüze bir kurulum ve dağıtım paketi ekleyin **Ekle**, **yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusundaki **yüklü** klasörü seçin **diğer proje türleri**, **Kurulum ve dağıtım**, **InstallShield Limited Edition**ve projenize bir ad verin. (İstenirse, indirin, yükleyin ve InstallShield etkinleştirin.)  
  
3.  Proje Asistanı kullanarak kurulum ve dağıtım projenizin genel yapılandırmasını gerçekleştirin **Çözüm Gezgini**, veya alt adımların numaralı adımları seçerek **Çözüm Gezgini**. Derlemeleri GAC'ye eklemekte değil, yaptığınız gibi kurulumunuzu yapılandırın.  
  
4.  GAC'ye bir derleme ekleme işlemine başlamak için seçin **dosyaları**, altında olduğu **uygulama verilerini belirtin** adımı **Çözüm Gezgini**.  
  
5.  İçinde **hedef bilgisayarın klasörleri** bölmesinde, kısayol menüsünü açın **hedef bilgisayar**ve ardından **önceden tanımlanmış klasörü Göster**, **[ GlobalAssemblyCache]**.  
  
6.  Çözümde yer alan ve genel derleme önbelleğine yüklemek istediğiniz bir derlemeyi içeren her bir proje için:  
  
    1.  İçinde **kaynak bilgisayarın klasörleri** bölmesinde projeyi seçin.  
  
    2.  İçinde **hedef bilgisayarın klasörleri** bölmesinde seçin **; [GlobalAssemblyCache]**.  
  
    3.  İçinde **kaynak bilgisayarın dosyaları** bölmesinde seçin **birincil çıktıyı** *< project_name >*.  
  
    4.  Adım C'deki dosyayı sürükleyin **hedef bilgisayarın dosyaları** bölmesinde (veya **kopyalama** ve **Yapıştır** komutları dosyanın kısayol menüsünden).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğinden Kaldırma](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Windows Installer dağıtımı](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
