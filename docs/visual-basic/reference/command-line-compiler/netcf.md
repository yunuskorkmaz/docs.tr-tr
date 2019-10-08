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
ms.openlocfilehash: 3df7e622f97a5a1291736180e3964b1b3deaea2f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005450"
---
# <a name="-netcf"></a>-netcf

.NET Compact Framework hedeflemek için derleyiciyi ayarlar.

## <a name="syntax"></a>Sözdizimi

```console
-netcf
```

## <a name="remarks"></a>Açıklamalar

@No__t-0 seçeneği, Visual Basic derleyicinin tam .NET Framework yerine .NET Compact Framework hedeflemesini sağlar. Yalnızca tam .NET Framework mevcut olan dil işlevselliği devre dışıdır.

@No__t-0 seçeneği [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)ile kullanılmak üzere tasarlanmıştır. @No__t-0 tarafından devre dışı bırakılan dil özellikleri, `-sdkpath` ile hedeflenen dosyalarda bulunmayan dil özellikleridir.

> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir. @No__t-0 seçeneği, bir Visual Basic cihaz projesi yüklendiğinde ayarlanır.

@No__t-0 seçeneği aşağıdaki dil özelliklerini değiştirir:

- Bir programın yürütülmesini sonlandıran [End \<Anahtar sözcüğü > deyimin](../../../visual-basic/language-reference/statements/end-keyword-statement.md) anahtar sözcüğü devre dışı bırakıldı. Aşağıdaki program `-netcf` olmadan derlenir ve çalışır, ancak `-netcf` ile derleme zamanında başarısız olur.

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Tüm formlarda geç bağlama devre dışıdır. Derleme zamanı hataları, tanınan geç bağlama senaryolarıyla karşılaşıldığında oluşturulur. Aşağıdaki program `-netcf` olmadan derlenir ve çalışır, ancak `-netcf` ile derleme zamanında başarısız olur.

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiricileri devre dışıdır. [Declare ifade](../../../visual-basic/language-reference/statements/declare-statement.md) ifadesinin sözdizimi de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` olarak değiştirilir. Aşağıdaki kod bir derlemede `-netcf` ' ın etkisini gösterir.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Visual Basic kaldırılmış Visual Basic 6,0 anahtar sözcüklerini kullanmak `-netcf` kullanıldığında farklı bir hata oluşturur. Bu, aşağıdaki anahtar sözcüklerin hata iletilerini etkiler:

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

Aşağıdaki kod, C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework `Myfile.vb` ' ı derler. Genellikle .NET Compact Framework en son sürümünü kullanırsınız.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
