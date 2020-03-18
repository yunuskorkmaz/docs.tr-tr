---
title: -publicsign (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662536"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="55d83-102">-publicsign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="55d83-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="55d83-103">Bu seçenek derleyicinin ortak bir anahtar uygulamasına neden olur, ancak derlemeyi gerçekte imzalamaz.</span><span class="sxs-lookup"><span data-stu-id="55d83-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="55d83-104">**-publicsign** seçeneği de dosyanın gerçekte imzalanmış olduğunu çalışma zamanı söyler derleme biraz ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55d83-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="55d83-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55d83-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="55d83-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="55d83-106">Arguments</span></span>

<span data-ttu-id="55d83-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="55d83-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="55d83-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55d83-108">Remarks</span></span>

<span data-ttu-id="55d83-109">**-publicsign** seçeneği [-keyfile](keyfile-compiler-option.md) veya [-keycontainer](keycontainer-compiler-option.md)kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="55d83-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="55d83-110">**Anahtar dosyası** veya **anahtar kapsayıcı** seçenekleri ortak anahtarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="55d83-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="55d83-111">**-publicsign** **ve-delaysign** seçenekleri birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="55d83-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="55d83-112">Bazen "sahte işaret" veya "OSS işareti" olarak adlandırılan, genel imza bir çıktı derlemesinde ortak anahtarı içerir ve "imzalı" bayrağı ayarlar, ancak aslında özel bir anahtarla derlemeyi imzalamaz.</span><span class="sxs-lookup"><span data-stu-id="55d83-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="55d83-113">Bu, insanların yayımlanan "tam olarak imzalanmış" derlemelerle uyumlu derlemeler oluşturmak istedikleri, ancak derlemeleri imzalamak için kullanılan özel anahtara erişemedikleri açık kaynak projeleri için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="55d83-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="55d83-114">Hemen hemen hiç tüketici aslında montaj tam olarak imzalanmış olup olmadığını kontrol etmek gerekir, bu kamuya inşa meclisleri tam olarak imzalanmış bir kullanılacak hemen hemen her senaryoda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55d83-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="55d83-115">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="55d83-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="55d83-116">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="55d83-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="55d83-117">Yalnızca **Gecikme işareti** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55d83-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="55d83-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55d83-118">See also</span></span>

- [<span data-ttu-id="55d83-119">C# Derleyici -delaysign işareti seçeneği</span><span class="sxs-lookup"><span data-stu-id="55d83-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="55d83-120">C# Derleyici -keyfile seçeneği</span><span class="sxs-lookup"><span data-stu-id="55d83-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="55d83-121">C# Derleyici -keycontainer seçeneği</span><span class="sxs-lookup"><span data-stu-id="55d83-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="55d83-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="55d83-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="55d83-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="55d83-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
