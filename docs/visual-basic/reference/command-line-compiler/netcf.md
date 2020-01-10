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
ms.openlocfilehash: 7f14ce07a2928f4dbffd3aa57f8cdd514b75694c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716711"
---
# <a name="-netcf"></a>-netcf

.NET Compact Framework hedeflemek için derleyiciyi ayarlar.

## <a name="syntax"></a>Sözdizimi

```console
-netcf
```

## <a name="remarks"></a>Açıklamalar

`-netcf` seçeneği, Visual Basic derleyicinin tam .NET Framework yerine .NET Compact Framework hedeflemesini sağlar. Yalnızca tam .NET Framework mevcut olan dil işlevselliği devre dışıdır.

`-netcf` seçeneği [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)ile kullanılmak üzere tasarlanmıştır. `-netcf` tarafından devre dışı bırakılan dil özellikleri, `-sdkpath`hedeflenen dosyalarda bulunmayan dil özellikleridir.

> [!NOTE]
> `-netcf` seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir. `-netcf` seçeneği, bir Visual Basic cihaz projesi yüklendiğinde ayarlanır.

`-netcf` seçeneği aşağıdaki dil özelliklerini değiştirir:

- Bir programın yürütülmesini sonlandıran [End \<anahtar sözcüğü > deyimin](../../../visual-basic/language-reference/statements/end-keyword-statement.md) anahtar sözcüğü devre dışı bırakıldı. Aşağıdaki program `-netcf` olmadan derlenir ve çalışır, ancak `-netcf`ile derleme zamanında başarısız olur.

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Tüm formlarda geç bağlama devre dışıdır. Derleme zamanı hataları, tanınan geç bağlama senaryolarıyla karşılaşıldığında oluşturulur. Aşağıdaki program `-netcf` olmadan derlenir ve çalışır, ancak `-netcf`ile derleme zamanında başarısız olur.

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiricileri devre dışıdır. [Declare ifadesinin](../../../visual-basic/language-reference/statements/declare-statement.md) sözdizimi de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`olarak değiştirilir. Aşağıdaki kod bir derlemede `-netcf` etkisini gösterir.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Visual Basic kaldırılmış Visual Basic 6,0 anahtar sözcüklerini kullanmak `-netcf` kullanıldığında farklı bir hata üretir. Bu, aşağıdaki anahtar sözcüklerin hata iletilerini etkiler:

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

Aşağıdaki kod, C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework `Myfile.vb` derler. Genellikle .NET Compact Framework en son sürümünü kullanırsınız.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
