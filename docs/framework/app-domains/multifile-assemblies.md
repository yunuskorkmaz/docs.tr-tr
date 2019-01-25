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
ms.openlocfilehash: bad63bbc8e221f306e5807f51fbbb8eb4761d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599185"
---
# <a name="multifile-assemblies"></a>Birden Çok Dosya Derlemeleri

Visual C++ ile komut satırı derleyicilerini veya Visual Studio kullanan çok dosyalı derlemeleri oluşturabilirsiniz. Derlemedeki bir dosya, derleme bildirimi içermelidir. Bir uygulamayı başlatan bir derleme ana veya WinMain yöntemi gibi bir giriş noktası da içermelidir.

Örneğin, iki kod modülleri, Client.cs ve Stringer.cs içeren bir uygulama olduğunu varsayalım. Stringer.cs oluşturur `myStringer` Client.cs kod tarafından başvurulan ad alanı. Client.cs içeren `Main` uygulamanın giriş noktası olan yöntem. Bu örnekte, iki kod modülleri derleyin ve ardından uygulamayı başlatan derleme bildirimini içeren üçüncü bir dosya oluşturun. Derleme bildirimi hem de başvuruda `Client` ve `Stringer` modüller.

> [!NOTE]
> Derlemenin birden çok kod modülleri olsa bile, birden çok dosya derlemeleri yalnızca bir giriş noktası olabilir.

Bir çoklu dosya derlemesi oluşturmak isteyebileceğiniz birkaç neden vardır:

-   Farklı dillerde yazılan modülleri birleştirmek için. Bir çoklu dosya derlemesi oluşturmak için en yaygın nedeni budur.

-   Nadiren kullanılan türleri yalnızca gerektiğinde indirilen bir modülün yerleştirerek bir uygulamanın indirilmesini optimize için.

    > [!NOTE]
    > Kullanılarak indirilen uygulamalar oluşturuyorsanız `<object>` etiketi Microsoft Internet Explorer kullanarak, çok dosyalı derlemeler oluşturmak önemlidir. Bu senaryoda, bir dosya yalnızca derleme bildirimi içeren kod modüllerinizi ayrı da oluşturun. Internet Explorer, derleme bildirimi ilk indirir ve ardından herhangi bir ek modüller veya gerekli derlemeleri yüklemek için çalışan iş parçacığı oluşturur. Internet Explorer, derleme bildirimini içeren dosya karşıdan yüklenirken kullanıcı girişine yanıt vermeyen olacaktır. Daha küçük derleme bildirimini içeren dosyayı, daha az zaman Internet Explorer yanıt vermeyen olacaktır.

-   Birden fazla geliştirici tarafından yazılan modülleri birleştirmek için. Her geliştirici her kod modülü bir derlemenin içine derleyebilirsiniz olsa da, bu tüm modüller, bir çoklu dosya derlemesi koyarsanız gösterilmez genel olarak açığa için bazı türleri zorlayabilirsiniz.

Derleme oluşturduktan sonra derleme bildirimini içeren dosyayı imzalayabilirsiniz (ve bu nedenle derleme), dosya (ve derleme) güçlü bir ad verin ve genel derleme önbelleğinde yerleştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)