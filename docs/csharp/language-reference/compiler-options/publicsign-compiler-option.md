---
description: -publicsign (C# derleyici seçenekleri)
title: -publicsign (C# derleyici seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124818"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="3ca40-103">-publicsign (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3ca40-103">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="3ca40-104">Bu seçenek derleyicinin ortak anahtar uygulamasına, ancak derlemeyi gerçekten imzalamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3ca40-104">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="3ca40-105">**-Publicsign** seçeneği Ayrıca derlemede, dosyanın gerçekten imzalandığını belirten bir bit belirler.</span><span class="sxs-lookup"><span data-stu-id="3ca40-105">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ca40-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3ca40-106">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="3ca40-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="3ca40-107">Arguments</span></span>

<span data-ttu-id="3ca40-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ca40-108">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ca40-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ca40-109">Remarks</span></span>

<span data-ttu-id="3ca40-110">**-Publicsign** seçeneği, [-keyfile](keyfile-compiler-option.md) veya [-keycontainer](keycontainer-compiler-option.md)kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3ca40-110">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="3ca40-111">**Keyfile** veya **keycontainer** seçenekleri ortak anahtarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ca40-111">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="3ca40-112">**-Publicsign** ve **-delaysign** seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="3ca40-112">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="3ca40-113">Bazen "sahte imza" veya "OSS işareti" olarak da adlandırılan ortak imzalama, bir çıktı derlemesinde ortak anahtarı içerir ve "imzalanmış" bayrağını ayarlar, ancak aslında derlemeyi özel bir anahtarla imzalayamıyor.</span><span class="sxs-lookup"><span data-stu-id="3ca40-113">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="3ca40-114">Bu, insanların yayınlanan "tam olarak imzalanmış" derlemeleriyle uyumlu derlemeler oluşturmak istediği, ancak derlemeleri imzalamak için kullanılan özel anahtara erişime sahip olmadığı açık kaynaklı projeler için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3ca40-114">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="3ca40-115">Neredeyse hiçbir tüketiciye derlemenin tamamen imzalanıp imzalanmadığını kontrol etmek zorunda olduğundan, bu genel olarak oluşturulan derlemeler neredeyse her bir senaryoda, tam olarak imzalanan bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ca40-115">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a><span data-ttu-id="3ca40-116">Bir csproj dosyasında bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3ca40-116">To set this compiler option in a csproj file</span></span>

<span data-ttu-id="3ca40-117">Bir proje için. csproj dosyasını açın ve şu öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3ca40-117">Open the .csproj file for a project, and add the following element:</span></span>

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a><span data-ttu-id="3ca40-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ca40-118">See also</span></span>

- [<span data-ttu-id="3ca40-119">C# derleyicisi-delaysign seçeneği</span><span class="sxs-lookup"><span data-stu-id="3ca40-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="3ca40-120">C# Derleyici-anahtar seçeneği</span><span class="sxs-lookup"><span data-stu-id="3ca40-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="3ca40-121">C# derleyicisi-keycontainer seçeneği</span><span class="sxs-lookup"><span data-stu-id="3ca40-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="3ca40-122">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="3ca40-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="3ca40-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="3ca40-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
