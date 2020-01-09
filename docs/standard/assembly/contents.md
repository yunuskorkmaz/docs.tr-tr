---
title: Derleme içerikleri
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345570"
---
# <a name="assembly-contents"></a>Derleme içerikleri

Genel olarak, statik bir derleme dört öğeden oluşabilir:

- Derleme meta verilerini içeren [bütünleştirilmiş kod bildirimi](manifest.md).

- Tür metaverileri.  

- Türleri uygulayan Microsoft ara dili (MSIL) kodu. Derleyici tarafından bir veya daha fazla kaynak kod dosyasından oluşturulur.

- Bir [kaynak](../../framework/resources/index.md)kümesi.  

Yalnızca derleme bildirimi gereklidir, ancak derlemeye herhangi bir anlamlı işlevsellik sağlamak için türler veya kaynaklar gereklidir.

Aşağıdaki çizimde, tek bir fiziksel dosyada gruplanmış olan bu öğeler gösterilmektedir:

![MyAssembly. dll adlı tek dosya derleme](./media/contents/single-file-assembly.gif)

Kaynak kodunuzu tasarlarken, uygulamanızın işlevselliğinin bir veya daha fazla dosyaya nasıl bölümleyeceğinize ilişkin açık kararlar alırsınız. .NET kodu tasarlarken, işlevselliği bir veya daha fazla derlemede nasıl bölümleyeceğinize ilişkin benzer kararlar alırsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Derleme bildirimi](manifest.md)
- [Bütünleştirilmiş kod güvenliği konuları](security-considerations.md)
