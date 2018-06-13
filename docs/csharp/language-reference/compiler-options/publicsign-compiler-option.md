---
title: -publicsign (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: ec25f9c1f2ef943db41bcfa20c8efd1d05866acd
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472854"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="96632-102">-publicsign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="96632-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="96632-103">Bu seçenek bir ortak anahtar uygulamak derleyici neden olur, ancak gerçekte derlemeyi imzalamak değil.</span><span class="sxs-lookup"><span data-stu-id="96632-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="96632-104">**- Publicsign** seçeneğini de ayarlar bir bit çalışma zamanı dosyası gerçekten imzalanmış söyler derlemede.</span><span class="sxs-lookup"><span data-stu-id="96632-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="96632-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96632-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="96632-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="96632-106">Arguments</span></span>

<span data-ttu-id="96632-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="96632-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="96632-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96632-108">Remarks</span></span>

<span data-ttu-id="96632-109">**- Publicsign** seçeneği kullanılmasını gerektiren [- keyfile](keyfile-compiler-option.md) veya [- keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="96632-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="96632-110">**Keyfile** veya **keycontainer** seçenekleri ortak anahtarı belirtin.</span><span class="sxs-lookup"><span data-stu-id="96632-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="96632-111">**- Publicsign** ve **- delaysign** seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="96632-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="96632-112">Bazen "sahte oturum" veya "OSS işareti" olarak adlandırılan, ortak imzalama çıkış bütünleştirilmiş ortak anahtarı içerir ve "imzalı" bayrağını ayarlar, ancak gerçekte derleme özel bir anahtarla oturum değil.</span><span class="sxs-lookup"><span data-stu-id="96632-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="96632-113">Bu kişiler yayımlanan "tam olarak imzalanmamış" derlemeler ile uyumludur, ancak derlemeler imzalamak için kullanılan özel anahtarı erişiminiz yoksa derlemeleri oluşturmak istediğiniz yere açık kaynak projeler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="96632-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="96632-114">Neredeyse hiçbir tüketicileri derleme tam olarak imzalanmamış denetlemek gerçekten gerekli olduğundan, bu genel olarak derlemeleri yerleşik burada tam olarak imzalanmış bir kullanılan neredeyse her senaryoda kullanışlı.</span><span class="sxs-lookup"><span data-stu-id="96632-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="96632-115">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="96632-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="96632-116">Açık **özellikleri** projesi için sayfa.</span><span class="sxs-lookup"><span data-stu-id="96632-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="96632-117">Değiştirme **gecikme yalnızca oturum** özelliği.</span><span class="sxs-lookup"><span data-stu-id="96632-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="96632-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96632-118">See Also</span></span>
 [<span data-ttu-id="96632-119">C# Derleyici - delaysign seçeneği</span><span class="sxs-lookup"><span data-stu-id="96632-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)  
 [<span data-ttu-id="96632-120">C# Derleyici - keyfile seçeneği</span><span class="sxs-lookup"><span data-stu-id="96632-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)  
 [<span data-ttu-id="96632-121">C# Derleyici - keycontainer seçeneği</span><span class="sxs-lookup"><span data-stu-id="96632-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)  
 [<span data-ttu-id="96632-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="96632-122">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="96632-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="96632-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
