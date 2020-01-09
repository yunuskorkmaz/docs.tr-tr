---
title: -nostdlib (C# derleyici seçenekleri)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345084"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="b26b1-102">-nostdlib (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b26b1-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="b26b1-103">**-nostdlib** , tüm sistem ad alanını tanımlayan mscorlib. dll ' nin içe aktarımını engeller.</span><span class="sxs-lookup"><span data-stu-id="b26b1-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="b26b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b26b1-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="b26b1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b26b1-105">Remarks</span></span>

<span data-ttu-id="b26b1-106">Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b26b1-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="b26b1-107">**-Nostdlib**belirtmezseniz, mscorlib. dll programınıza içeri aktarılır ( **-nostdlib-** belirtilerek aynı).</span><span class="sxs-lookup"><span data-stu-id="b26b1-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="b26b1-108">**-Nostdlib** belirtildiğinde **-nostdlib +** belirtilerek aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b26b1-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="b26b1-109">Visual Studio 'da Bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b26b1-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="b26b1-110">Aşağıdaki yönergeler yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b26b1-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="b26b1-111">**Mscorlib. dll derleme özelliğine başvurulmayın** , Visual Studio 'nun daha yeni sürümlerinde bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="b26b1-111">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="b26b1-112">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="b26b1-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="b26b1-113">**Yapı** özellikleri sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b26b1-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="b26b1-114">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b26b1-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="b26b1-115">**Mscorlib. dll ' nin başvurmayın** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b26b1-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="b26b1-116">Bu derleyici seçeneğini program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b26b1-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="b26b1-117">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="b26b1-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b26b1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b26b1-118">See also</span></span>

- [<span data-ttu-id="b26b1-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b26b1-119">C# Compiler Options</span></span>](./index.md)
