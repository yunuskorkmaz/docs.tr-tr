---
title: -nostdlib (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: cf87d8d2ac4531142288a8637f7fbeb9139382ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662653"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="54263-102">-nostdlib (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="54263-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="54263-103">**-nostdlib** tüm sistem ad alanını tanımlayan mscorlib.dll alma engeller.</span><span class="sxs-lookup"><span data-stu-id="54263-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="54263-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54263-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="54263-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54263-105">Remarks</span></span>

<span data-ttu-id="54263-106">Tanımlayın veya kendi sistem ad alanı ve nesneler oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="54263-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="54263-107">Siz belirtmezseniz **- nostdlib**, mscorlib.dll programınız alınır (belirtmekle aynı **- nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="54263-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="54263-108">Belirtme **- nostdlib** belirtmekle aynı **- nostdlib +**.</span><span class="sxs-lookup"><span data-stu-id="54263-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="54263-109">Bu derleyici seçeneğini Visual Studio'da ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="54263-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="54263-110">Visual Studio 2015 (ve önceki sürümleri) aşağıdaki yönergeleri uygulamak yalnızca.</span><span class="sxs-lookup"><span data-stu-id="54263-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="54263-111">**Mscorlib.dll dosyasına başvurma** yapı özelliği, Visual Studio 2017'de yok.</span><span class="sxs-lookup"><span data-stu-id="54263-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="54263-112">Açık **özellikleri** proje sayfası.</span><span class="sxs-lookup"><span data-stu-id="54263-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="54263-113">Tıklayın **derleme** Özellikler sayfası.</span><span class="sxs-lookup"><span data-stu-id="54263-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="54263-114">Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="54263-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="54263-115">Değiştirme **mscorlib.dll dosyasına başvurma** özelliği.</span><span class="sxs-lookup"><span data-stu-id="54263-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="54263-116">Bu derleyici seçeneğini program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="54263-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="54263-117">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="54263-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="54263-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54263-118">See also</span></span>

- [<span data-ttu-id="54263-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="54263-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
