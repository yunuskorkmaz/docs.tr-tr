---
title: Çoklu dosya derlemeleri
ms.date: 08/20/2019
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
ms.openlocfilehash: b4c288a54194e89eb90b6ac512cf45184376e952
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971872"
---
# <a name="multifile-assemblies"></a>Çoklu dosya derlemeleri

Komut satırı derleyicileri veya Visual C++Studio 'yu kullanarak .NET Framework hedefleyen çok dosyalı derlemeler oluşturabilirsiniz. Derlemedeki bir dosyanın derleme bildirimini içermesi gerekir. Bir uygulamayı başlatan bir derleme, `Main` ya `WinMain` da yöntemi gibi bir giriş noktası içermelidir.

Örneğin, *Client.cs* ve *Stringer.cs*olmak üzere iki kod modülü içeren bir uygulamanız olduğunu varsayalım. *Stringer.cs* , `myStringer` *Client.cs*içindeki kod tarafından başvurulan ad alanını oluşturur. *Client.cs* , uygulamanın `Main` giriş noktası olan yöntemini içerir. Bu örnekte, iki kod modülünü derler ve ardından uygulamayı başlatan derleme bildirimini içeren üçüncü bir dosya oluşturursunuz. Derleme bildirimi hem *istemci* hem de *stru* modüllerine başvurur.

> [!NOTE]
> Çok dosyalı derlemeler, derleme birden fazla kod modüllerine sahip olsa bile yalnızca bir giriş noktasına sahip olabilir.

Çok dosyalı bir derleme oluşturmak isteyebileceğiniz birkaç neden vardır:

- Farklı dillerde yazılmış modülleri birleştirmek için. Bu, çok dosyalı bir derleme oluşturmanın en yaygın nedenidir.

- Nadiren kullanılan türleri yalnızca gerektiğinde indirilen bir modüle yerleştirerek, bir uygulamayı indirmeyi iyileştirmek için.

    > [!NOTE]
    > Microsoft Internet Explorer ile `<object>` etiketi kullanılarak indirilecek uygulamalar oluşturuyorsanız, çok dosyalı derlemeler oluşturmanız önemlidir. Bu senaryoda, yalnızca derleme bildirimini içeren kod modüllerinizden ayrı bir dosya oluşturursunuz. Internet Explorer önce derleme bildirimini indirir ve ardından gereken ek modülleri veya derlemeleri indirmek için çalışan iş parçacıkları oluşturur. Derleme bildirimini içeren dosya indirilirken, Internet Explorer kullanıcı girişine yanıt vermez. Derleme bildirimini içeren dosya ne kadar küçükse Internet Explorer yanıt vermemeye karşı daha az zaman olur.

- Çeşitli geliştiriciler tarafından yazılan kod modüllerini birleştirmek için. Her geliştirici her kod modülünü bir derlemede derleyebilse de, bu, tüm modüller çok dosyalı bir derlemeye yerleştirilse, bazı türlerin herkese açık bir şekilde gösterilmesini zorlayabilir.

Derlemeyi oluşturduktan sonra, derleme bildirimini içeren dosyayı imzalayabilir ve bu nedenle derleme yapabilir ya da dosyaya ve derlemeye tanımlayıcı bir ad verebilir ve bunu genel derleme önbelleğine yerleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Çoklu dosya derlemesi oluşturma](build-multifile-assembly.md)
- [Bütünleştirilmiş kod içeren program](../../standard/assembly/program.md)
