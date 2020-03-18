---
title: -nostdlib (C# Derleyici Seçenekleri)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345084"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="be3bd-102">-nostdlib (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="be3bd-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="be3bd-103">**-nostdlib** tüm Sistem ad alanını tanımlayan mscorlib.dll'nin ithalatını önler.</span><span class="sxs-lookup"><span data-stu-id="be3bd-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="be3bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be3bd-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="be3bd-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be3bd-105">Remarks</span></span>

<span data-ttu-id="be3bd-106">Kendi Sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="be3bd-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="be3bd-107">**-nostdlib,** mscorlib.dll belirtmezseniz programınıza alınır **(-nostdlib-** belirtilmesi yle aynıdır).</span><span class="sxs-lookup"><span data-stu-id="be3bd-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="be3bd-108">**-nostdlib** belirtme **-nostdlib+** belirterek aynıdır.</span><span class="sxs-lookup"><span data-stu-id="be3bd-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="be3bd-109">Visual Studio'da bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="be3bd-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="be3bd-110">Aşağıdaki talimatlar yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="be3bd-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="be3bd-111">**Do not reference mscorlib.dll** build özelliği Visual Studio'nun yeni sürümlerinde yok.</span><span class="sxs-lookup"><span data-stu-id="be3bd-111">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="be3bd-112">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="be3bd-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="be3bd-113">Özellikleri **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="be3bd-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="be3bd-114">**Gelişmiş** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="be3bd-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="be3bd-115">**Mscorlib.dll** özelliğine başvuru yapma özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="be3bd-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="be3bd-116">Bu derleyici seçeneğini program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="be3bd-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="be3bd-117">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A></span><span class="sxs-lookup"><span data-stu-id="be3bd-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="be3bd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be3bd-118">See also</span></span>

- [<span data-ttu-id="be3bd-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="be3bd-119">C# Compiler Options</span></span>](./index.md)
