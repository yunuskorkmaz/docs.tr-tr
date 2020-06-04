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
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397481"
---
# <a name="-netcf"></a>-netcf

.NET Compact Framework hedeflemek için derleyiciyi ayarlar.

## <a name="syntax"></a>Sözdizimi

```console
-netcf
```

## <a name="remarks"></a>Açıklamalar

`-netcf`Seçeneği, Visual Basic derleyicisinin tam .NET Framework yerine .NET Compact Framework hedeflemesini sağlar. Yalnızca tam .NET Framework mevcut olan dil işlevselliği devre dışıdır.

`-netcf`Seçeneği [-SdkPath](sdkpath.md)ile kullanılmak üzere tasarlanmıştır. Tarafından devre dışı bırakılan dil özellikleri, `-netcf` ile hedeflenen dosyalarda mevcut olmayan dil özellikleridir `-sdkpath` .

> [!NOTE]
> `-netcf`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir. `-netcf`Visual Basic bir cihaz projesi yüklendiğinde bu seçenek ayarlanır.

`-netcf`Seçeneği aşağıdaki dil özelliklerini değiştirir:

- Bir programın yürütülmesini sonlandıran [End \<keyword> deyimin](../../language-reference/statements/end-keyword-statement.md) anahtar sözcüğü devre dışı bırakıldı. Aşağıdaki program, `-netcf` ile derleme zamanında derleyip çalışır, ancak başarısız olur `-netcf` .

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Tüm formlarda geç bağlama devre dışıdır. Derleme zamanı hataları, tanınan geç bağlama senaryolarıyla karşılaşıldığında oluşturulur. Aşağıdaki program, `-netcf` ile derleme zamanında derleyip çalışır, ancak başarısız olur `-netcf` .

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Auto](../../language-reference/modifiers/auto.md), [ANSI](../../language-reference/modifiers/ansi.md)ve [Unicode](../../language-reference/modifiers/unicode.md) değiştiricileri devre dışıdır. [Declare ifadesinin](../../language-reference/statements/declare-statement.md) sözdizimi de olarak değiştirilir `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` . Aşağıdaki kod, derleme üzerinde etkisini gösterir `-netcf` .

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Visual Basic kaldırılmış Visual Basic 6,0 anahtar sözcüklerini kullanmak kullanıldığında farklı bir hata oluşturur `-netcf` . Bu, aşağıdaki anahtar sözcüklerin hata iletilerini etkiler:

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

Aşağıdaki kod, `Myfile.vb` C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework ile derlenir. Genellikle .NET Compact Framework en son sürümünü kullanırsınız.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)
