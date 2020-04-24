---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005284"
---
# <a name="-quiet"></a><span data-ttu-id="ae088-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="ae088-102">-quiet</span></span>

<span data-ttu-id="ae088-103">Derleyicinin sözdizimiyle ilgili hatalar ve uyarılar için kod görüntülemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="ae088-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae088-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae088-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="ae088-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae088-105">Remarks</span></span>

<span data-ttu-id="ae088-106">Varsayılan `-quiet` olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="ae088-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="ae088-107">Derleyici söz dizimi ile ilgili bir hata veya uyarı bildirdiğinde, satır kaynak kodundan de çıkış olur.</span><span class="sxs-lookup"><span data-stu-id="ae088-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="ae088-108">Derleyici çıkışını ayrıştırmaya yönelik uygulamalar için derleyicinin yalnızca Tanılamanın metnini çıktısının daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae088-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="ae088-109">Aşağıdaki örnekte, `Module1` olmadan `-quiet`derlendiğinde kaynak kodu içeren bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="ae088-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="ae088-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="ae088-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="ae088-111">İle `-quiet`derlenirse, derleyici yalnızca aşağıdakilerin çıktısını verir:</span><span class="sxs-lookup"><span data-stu-id="ae088-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="ae088-112">Bu `-quiet` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae088-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="ae088-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae088-113">Example</span></span>

<span data-ttu-id="ae088-114">Aşağıdaki kod, sözdizimi `T2.vb` ile ilgili derleyici tanılamaları için kodu derler ve görüntülemez:</span><span class="sxs-lookup"><span data-stu-id="ae088-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="ae088-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae088-115">See also</span></span>

- [<span data-ttu-id="ae088-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ae088-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ae088-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ae088-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
