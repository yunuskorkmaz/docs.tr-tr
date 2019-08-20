---
title: -nostdlib (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 486539d7abdc3e65847a0bc0e228b1b20a2b2c37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602693"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="2ce45-102">-nostdlib (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2ce45-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="2ce45-103">**-nostdlib** , tüm sistem ad alanını tanımlayan mscorlib. dll ' nin içe aktarımını engeller.</span><span class="sxs-lookup"><span data-stu-id="2ce45-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ce45-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ce45-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="2ce45-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ce45-105">Remarks</span></span>

<span data-ttu-id="2ce45-106">Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ce45-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="2ce45-107">**-Nostdlib**belirtmezseniz, mscorlib. dll programınıza içeri aktarılır ( **-nostdlib-** belirtilerek aynı).</span><span class="sxs-lookup"><span data-stu-id="2ce45-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="2ce45-108">**-Nostdlib** belirtildiğinde **-nostdlib +** belirtilerek aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2ce45-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="2ce45-109">Visual Studio 'da Bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2ce45-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="2ce45-110">Aşağıdaki yönergeler yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2ce45-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="2ce45-111">Visual Studio 2017 ' de **mscorlib. dll** derlemesi oluşturma özelliği yok.</span><span class="sxs-lookup"><span data-stu-id="2ce45-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="2ce45-112">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="2ce45-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="2ce45-113">**Yapı** özellikleri sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2ce45-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="2ce45-114">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2ce45-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="2ce45-115">**Mscorlib. dll ' nin başvurmayın** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2ce45-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="2ce45-116">Bu derleyici seçeneğini program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2ce45-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="2ce45-117">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ce45-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ce45-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ce45-118">See also</span></span>

- [<span data-ttu-id="2ce45-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2ce45-119">C# Compiler Options</span></span>](./index.md)
