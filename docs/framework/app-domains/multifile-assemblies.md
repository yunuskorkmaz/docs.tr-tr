---
title: Birden çok dosyalı derlemeler
description: Komut satırı derleyicilerini veya Visual C++ ile Visual Studio 'Yu kullanarak .NET 'i hedefleyen çok dosyalı derlemeler kullanın. Derlemedeki bir dosya, derleme bildirimini tutamalıdır.
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
ms.openlocfilehash: a5fb41b3b136a325e6b8658da521cba3176e929f
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104643"
---
# <a name="multifile-assemblies"></a>Birden çok dosyalı derlemeler

Visual C++ komut satırı derleyicilerini veya Visual Studio 'Yu kullanarak .NET Framework hedefleyen çok dosyalı derlemeler oluşturabilirsiniz. Derlemedeki bir dosyanın derleme bildirimini içermesi gerekir. Bir uygulamayı başlatan bir derleme, ya da yöntemi gibi bir giriş noktası içermelidir `Main` `WinMain` .

Örneğin, *Client.cs* ve *Stringer.cs*olmak üzere iki kod modülü içeren bir uygulamanız olduğunu varsayalım. *Stringer.cs* , `myStringer` *Client.cs*içindeki kod tarafından başvurulan ad alanını oluşturur. *Client.cs* , `Main` uygulamanın giriş noktası olan yöntemini içerir. Bu örnekte, iki kod modülünü derler ve ardından uygulamayı başlatan derleme bildirimini içeren üçüncü bir dosya oluşturursunuz. Derleme bildirimi hem *istemci* hem de *stru* modüllerine başvurur.

> [!NOTE]
> Çok dosyalı derlemeler, derleme birden fazla kod modüllerine sahip olsa bile yalnızca bir giriş noktasına sahip olabilir.

Çok dosyalı bir derleme oluşturmak isteyebileceğiniz birkaç neden vardır:

- Farklı dillerde yazılmış modülleri birleştirmek için. Bu, çok dosyalı bir derleme oluşturmanın en yaygın nedenidir.

- Nadiren kullanılan türleri yalnızca gerektiğinde indirilen bir modüle yerleştirerek, bir uygulamayı indirmeyi iyileştirmek için.

    > [!NOTE]
    > `<object>`Microsoft Internet Explorer ile etiketi kullanılarak indirilecek uygulamalar oluşturuyorsanız, çok dosyalı derlemeler oluşturmanız önemlidir. Bu senaryoda, yalnızca derleme bildirimini içeren kod modüllerinizden ayrı bir dosya oluşturursunuz. Internet Explorer önce derleme bildirimini indirir ve ardından gereken ek modülleri veya derlemeleri indirmek için çalışan iş parçacıkları oluşturur. Derleme bildirimini içeren dosya indirilirken, Internet Explorer kullanıcı girişine yanıt vermez. Derleme bildirimini içeren dosya ne kadar küçükse Internet Explorer yanıt vermemeye karşı daha az zaman olur.

- Çeşitli geliştiriciler tarafından yazılan kod modüllerini birleştirmek için. Her geliştirici her kod modülünü bir derlemede derleyebilse de, bu, tüm modüller çok dosyalı bir derlemeye yerleştirilse, bazı türlerin herkese açık bir şekilde gösterilmesini zorlayabilir.

Derlemeyi oluşturduktan sonra, derleme bildirimini içeren dosyayı imzalayabilir ve bu nedenle derleme yapabilir ya da dosyaya ve derlemeye tanımlayıcı bir ad verebilir ve bunu genel derleme önbelleğine yerleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Birden çok dosyalı derleme oluşturma](build-multifile-assembly.md)
- [Derlemeler ile programlama](../../standard/assembly/index.md)
