---
description: -nostdlib (C# derleyici seçenekleri)
title: -nostdlib (C# derleyici seçenekleri)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125104"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="5592d-103">-nostdlib (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5592d-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="5592d-104">**-nostdlib** , tüm sistem ad alanını tanımlayan mscorlib.dll içeri aktarmayı engeller.</span><span class="sxs-lookup"><span data-stu-id="5592d-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="5592d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5592d-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="5592d-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5592d-106">Remarks</span></span>

<span data-ttu-id="5592d-107">Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="5592d-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="5592d-108">**-Nostdlib**belirtmezseniz, mscorlib.dll programınıza içeri aktarılır ( **-nostdlib-** belirtilerek aynı).</span><span class="sxs-lookup"><span data-stu-id="5592d-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="5592d-109">**-Nostdlib** belirtildiğinde **-nostdlib +** belirtilerek aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5592d-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="5592d-110">Visual Studio 'da Bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5592d-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="5592d-111">Aşağıdaki yönergeler yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5592d-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="5592d-112">**Reference mscorlib.dll** Build özelliği, Visual Studio 'nun daha yeni sürümlerinde bulunmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="5592d-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="5592d-113">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="5592d-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="5592d-114">**Yapı** özellikleri sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5592d-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="5592d-115">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5592d-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="5592d-116">**Başvurmayın mscorlib.dll** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5592d-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="5592d-117">Bu derleyici seçeneğini program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5592d-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="5592d-118">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A> ..</span><span class="sxs-lookup"><span data-stu-id="5592d-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5592d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5592d-119">See also</span></span>

- [<span data-ttu-id="5592d-120">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5592d-120">C# Compiler Options</span></span>](./index.md)
