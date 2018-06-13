---
title: Birden Çok Dosya Derlemeleri
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8612e8d598e7f92cd9fc0106f99d21a239db90b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742516"
---
# <a name="multifile-assemblies"></a>Birden Çok Dosya Derlemeleri
Komut satırı derleyicileri kullanarak birden çok dosya derlemeleri oluşturabilir veya [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] Visual C++ ile. Derleme bildirimi derlemesindeki bir dosya içermelidir. Bir uygulamayı başlatır bütünleştirilmiş bir ana veya WinMain yöntemi gibi bir giriş noktası da içermelidir.  
  
 Örneğin, iki kod modülleri, Client.cs ve Stringer.cs içeren bir uygulama olduğunu varsayalım. Stringer.cs oluşturur `myStringer` Client.cs kod tarafından başvurulan ad alanı. Client.cs içeren `Main` uygulamanın giriş noktasıdır yöntemi. Bu örnekte, iki kod modüllerini derleyin ve ardından uygulamayı başlatan derleme bildirimi içeren üçüncü bir dosya oluşturun. Derleme bildirimi her ikisi de başvuran `Client` ve `Stringer` modüller.  
  
> [!NOTE]
>  Derleme birden çok kod modülleri olsa bile, birden çok dosya derlemeleri yalnızca bir giriş noktası, olabilir.  
  
 Birden fazla dosya derlemesi oluşturmak isteyebilirsiniz birkaç nedeni vardır:  
  
-   Farklı dillerde yazılmış modüller birleştirmek için. Birden fazla dosya derlemesi oluşturmak için en yaygın nedeni budur.  
  
-   Bir uygulamayı yalnızca gerekli olduğunda indirilen modülde nadiren kullanılan türleri koyarak indirme en iyi duruma getirme.  
  
    > [!NOTE]
    >  Kullanarak yüklenecek uygulamaları oluşturuyorsanız `<object>` etiketi Microsoft Internet Explorer ile birden çok dosya derlemeleri oluşturmak önemlidir. Bu senaryoda, bir dosyayı yalnızca derleme bildirimi içerir, kod modülleri ayrı da oluşturun. Internet Explorer derleme bildirimi ilk indirir ve daha sonra herhangi bir ek modüller veya gerekli derlemeleri indirmek için çalışan iş parçacığı oluşturur. Derleme bildirimi içeren dosyası indirilirken, Internet Explorer kullanıcı girişine yanıt vermeyen olacaktır. Daha küçük derleme bildirimi içeren dosyayı, daha az zaman Internet Explorer yanıt vermeyen olacaktır.  
  
-   Kod modülleri birkaç Geliştiricileriniz tarafından geliştirilen birleştirmek için. Her geliştirici bir derlemeye her kod modülü derleyebilirsiniz karşın, bu tüm modülleri birden çok dosya derlemeye yerleştirirseniz sunulmaz genel olarak açığa çıkarılması bazı türleri zorlayabilirsiniz.  
  
 Derleme oluşturduktan sonra derleme bildirimi içeren dosyayı imzalayabilirsiniz (ve bu nedenle derleme), ya da dosyasını (ve derleme) güçlü bir ad verin ve genel derleme önbelleğinde yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
