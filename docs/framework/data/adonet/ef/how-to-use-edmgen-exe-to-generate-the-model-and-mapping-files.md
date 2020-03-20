---
title: 'Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: ee8297c0833378b2b44800355b47db9caa2dc7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150525"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma
Bu konu, Okul veritabanına dayalı aşağıdaki dosyaları oluşturmak için EDM Generator (EdmGen.exe) aracının nasıl kullanılacağını gösterir:  
  
- Kavramsal bir model (.csdl dosyası).  
  
- Depolama modeli (.ssdl dosyası).  
  
- Kavramsal ve depolama modelleri (.msl dosyası) arasında eşleme.  
  
- Visual Basic veya C#'da nesne katmanı kodu.  
  
- Dosyaları görüntüleyin.  
  
 EdmGen.exe aracı, yukarıda listelenen dosyaları oluşturmak için /mode:FullGeneration kullanır. EdmGen.exe komutları hakkında daha fazla bilgi için [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md)bakın.  
  
 Modeli ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanıyorsanız, Yine de Entity Framework'i kullanmak için Visual Studio projenizi yapılandırmanız gerekir. Daha fazla bilgi için [bkz: Varlık Çerçeve Projesi'ni el ile yapılandırın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))  
  
> [!NOTE]
> EdmGen.exe tarafından oluşturulan kavramsal bir model veritabanındaki tüm nesneleri içerir. Yalnızca belirli nesneleri içeren kavramsal bir model oluşturmak istiyorsanız, Varlık Veri Modeli Sihirbazı'nı kullanın. Daha fazla bilgi için [bkz: Varlık Veri Modeli Sihirbazı'nı kullanın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe kullanarak Visual Basic projesi için Okul modelini oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))  
  
2. Komut isteminde, satır sonları olmadan aşağıdaki komutu uygulayın:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen.exe kullanarak bir C# projesi için Okul modelini oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))  
  
2. Komut isteminde, satır sonları olmadan aşağıdaki komutu uygulayın:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Modelleme ve Eşleme](modeling-and-mapping.md)
- [Nasıl?](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Nasıl yapilir: Sorgu Performansını Artırmak için Görünümleri Önceden Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET Varlık Veri Modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
