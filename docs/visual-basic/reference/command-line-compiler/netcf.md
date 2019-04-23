---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: d7c3bcba8e62d62904ed778a48d0e8ae6738ce00
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480774"
---
# <a name="-netcf"></a>-netcf

Derleyicinin hedef ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].

## <a name="syntax"></a>Sözdizimi

```
-netcf
```

## <a name="remarks"></a>Açıklamalar

`-netcf` Seçeneği neden olur, Visual Basic Derleyicisi hedef [!INCLUDE[Compact](~/includes/compact-md.md)] tam yerine [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Yalnızca tam olarak mevcut olan dil işlevleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] devre dışı bırakıldı.

`-netcf` Seçeneği ile kullanılmak üzere tasarlanmıştır [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Devre dışı dil özellikleri `-netcf` aynı dil özellikleri ile hedeflenen dosyalarda mevcut olan `-sdkpath`.

> [!NOTE]
> `-netcf` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir. `-netcf` Seçeneği, Visual Basic cihaz projesi yüklendiğinde ayarlanır.

`-netcf` Seçeneği aşağıdaki dil özellikleri değiştirir:

- [Son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) anahtar sözcüğü bir programın yürütülmesini sonlandıran, devre dışı bırakıldı. Aşağıdaki programın olmadan çalışır ve `-netcf` ile derleme zamanında başarısız olduğunda `-netcf`.

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Geç bağlama, tüm formları içinde devre dışı bırakıldı. Tanınan geç bağlama senaryoları karşılaştı, derleme zamanı hatalarına üretilir. Aşağıdaki programın olmadan çalışır ve `-netcf` ile derleme zamanında başarısız olduğunda `-netcf`.

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Otomatik](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md), ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiriciler devre dışı bırakıldı. Söz dizimi [Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) deyimi için değişiklik de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Aşağıdaki kod etkisini gösterir `-netcf` bir derleme üzerinde.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Visual Basic kaldırılan Visual Basic 6.0 anahtar sözcüklerini kullanarak, farklı bir hata oluşturur, `-netcf` kullanılır. Bu, aşağıdaki anahtar sözcükler için hata iletileri etkiler:

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a>Örnek

Aşağıdaki kod derlenir `Myfile.vb` ile [!INCLUDE[Compact](~/includes/compact-md.md)], mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin sürümlerini kullanarak varsayılan yükleme dizininde bulunan [!INCLUDE[Compact](~/includes/compact-md.md)] C sürücüsünde. Genellikle, en son sürümünü kullanın [!INCLUDE[Compact](~/includes/compact-md.md)].

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
