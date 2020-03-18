---
title: Derleme içerikleri
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75345570"
---
# <a name="assembly-contents"></a>Derleme içerikleri

Genel olarak, statik bir derleme dört öğeden oluşabilir:

- Derleme meta verilerini içeren [derleme bildirimi.](manifest.md)

- Tür metaverileri.  

- Türleri uygulayan Microsoft ara dili (MSIL) kodu. Derleyici tarafından bir veya daha fazla kaynak kod dosyasından oluşturulur.

- Bir dizi [kaynak.](../../framework/resources/index.md)  

Yalnızca derleme bildirimi gereklidir, ancak derlemeye herhangi bir anlamlı işlevsellik sağlamak için türler veya kaynaklar gereklidir.

Aşağıdaki resimde, tek bir fiziksel dosyada gruplanmış bu öğeler gösterilmektedir:

![MyAssembly.dll adlı tek dosyalı bir derleme](./media/contents/single-file-assembly.gif)

Kaynak kodunuzu tasarlarken, uygulamanızın işlevselliğini bir veya daha fazla dosyaya bölme konusunda açık kararlar verirsiniz. .NET kodunu tasarlarken, işlevselliği bir veya daha fazla derlemeye bölme konusunda benzer kararlar alabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Montaj manifestosu](manifest.md)
- [Derleme güvenliği hakkında dikkate alınması gerekenler](security-considerations.md)
