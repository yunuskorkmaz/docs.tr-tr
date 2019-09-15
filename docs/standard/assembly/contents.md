---
title: Bütünleştirilmiş kod içeriği
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d9268b0ec1ea919730a2ebcd209507692284cc6
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973378"
---
# <a name="assembly-contents"></a>Bütünleştirilmiş kod içeriği
Genel olarak, statik bir derleme dört öğeden oluşabilir:

- Derleme meta verilerini içeren [bütünleştirilmiş kod bildirimi](manifest.md).

- Tür metaverileri.  

- Türleri uygulayan Microsoft ara dili (MSIL) kodu. Derleyici tarafından bir veya daha fazla kaynak kod dosyasından oluşturulur.

- Bir kaynak kümesi.  

Yalnızca derleme bildirimi gereklidir, ancak derlemeye herhangi bir anlamlı işlevsellik sağlamak için türler veya kaynaklar gereklidir.

Aşağıdaki çizim, tek bir fiziksel dosyada gruplanmış olan bu öğeleri gösterir.

![MyAssembly. dll adlı tek dosya derlemesini gösteren diyagram.](./media/contents/single-file-assembly.gif)

Bu görselde, üç dosya da MyAssembly.dll içindeki derleme bildiriminde açıklandığı şekilde bir derlemede bulunmaktadır. Dosya sistemi açısından üç ayrı dosyadırlar. Util.netmodule dosyası hiçbir derleme bilgisi içermediğinden, bu dosyanın bir modül olarak derlendiğini unutmayın. Derleme oluşturulduğunda derleme bildirimi MyAssembly.dll içine eklenerek Util.netmodule ve Graphic.bmp ile olan ilişkisini belirtir.

Kaynak kodunuzu tasarlarken, uygulamanızın işlevselliğini bir veya daha fazla dosyaya nasıl ayıracağınız hakkında açık kararlar verirsiniz. .NET Framework kodu tasarlarken, işlevselliği bir veya daha fazla derlemeye nasıl ayıracağınız hakkında da benzer kararlar verirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Derleme bildirimi](manifest.md)
- [Bütünleştirilmiş kod güvenliği konuları](security-considerations.md)
