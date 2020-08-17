---
title: -publicsign (C# derleyici seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 2655e0216a412053e052ab2ec2fcc8c68ea4f968
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268055"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="417c9-102">-publicsign (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="417c9-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="417c9-103">Bu seçenek derleyicinin ortak anahtar uygulamasına, ancak derlemeyi gerçekten imzalamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="417c9-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="417c9-104">**-Publicsign** seçeneği Ayrıca derlemede, dosyanın gerçekten imzalandığını belirten bir bit belirler.</span><span class="sxs-lookup"><span data-stu-id="417c9-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="417c9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="417c9-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="417c9-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="417c9-106">Arguments</span></span>

<span data-ttu-id="417c9-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="417c9-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="417c9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="417c9-108">Remarks</span></span>

<span data-ttu-id="417c9-109">**-Publicsign** seçeneği, [-keyfile](keyfile-compiler-option.md) veya [-keycontainer](keycontainer-compiler-option.md)kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="417c9-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="417c9-110">**Keyfile** veya **keycontainer** seçenekleri ortak anahtarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="417c9-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="417c9-111">**-Publicsign** ve **-delaysign** seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="417c9-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="417c9-112">Bazen "sahte imza" veya "OSS işareti" olarak da adlandırılan ortak imzalama, bir çıktı derlemesinde ortak anahtarı içerir ve "imzalanmış" bayrağını ayarlar, ancak aslında derlemeyi özel bir anahtarla imzalayamıyor.</span><span class="sxs-lookup"><span data-stu-id="417c9-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="417c9-113">Bu, insanların yayınlanan "tam olarak imzalanmış" derlemeleriyle uyumlu derlemeler oluşturmak istediği, ancak derlemeleri imzalamak için kullanılan özel anahtara erişime sahip olmadığı açık kaynaklı projeler için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="417c9-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="417c9-114">Neredeyse hiçbir tüketiciye derlemenin tamamen imzalanıp imzalanmadığını kontrol etmek zorunda olduğundan, bu genel olarak oluşturulan derlemeler neredeyse her bir senaryoda, tam olarak imzalanan bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="417c9-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a><span data-ttu-id="417c9-115">Bir csproj dosyasında bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="417c9-115">To set this compiler option in a csproj file</span></span>

<span data-ttu-id="417c9-116">Bir proje için. csproj dosyasını açın ve şu öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="417c9-116">Open the .csproj file for a project, and add the following element:</span></span>

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a><span data-ttu-id="417c9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="417c9-117">See also</span></span>

- [<span data-ttu-id="417c9-118">C# derleyicisi-delaysign seçeneği</span><span class="sxs-lookup"><span data-stu-id="417c9-118">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="417c9-119">C# Derleyici-anahtar seçeneği</span><span class="sxs-lookup"><span data-stu-id="417c9-119">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="417c9-120">C# derleyicisi-keycontainer seçeneği</span><span class="sxs-lookup"><span data-stu-id="417c9-120">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="417c9-121">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="417c9-121">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="417c9-122">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="417c9-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
