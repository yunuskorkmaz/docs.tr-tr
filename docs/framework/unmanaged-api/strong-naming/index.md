---
title: Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7e431f3a41fadb7247f20d7ab9bb9120e827b0cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732300"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="639d3-102">Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="639d3-102">Strong Naming (Unmanaged API Reference)</span></span>

<span data-ttu-id="639d3-103">Güçlü adlandırma API 'SI, bir istemcinin derlemeler için tanımlayıcı ad imzalamayı yönetmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="639d3-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="639d3-104">Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler.</span><span class="sxs-lookup"><span data-stu-id="639d3-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="639d3-105">Tanımlayıcı ad imzalama, ad benzersizliği doğrulamaya yardımcı olur, ad yanıltmasını önler ve bir başvuru çözüldüğünde çağıranlar benzersiz bir kimlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="639d3-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="639d3-106">Ancak, tanımlayıcı bir adla ilişkili güven düzeyi yoktur.</span><span class="sxs-lookup"><span data-stu-id="639d3-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="639d3-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="639d3-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="639d3-108">Bu işlevlerin tümü .NET Framework 4 ' den itibaren kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="639d3-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="639d3-109">Önerilen alternatifler için [ICLRStrongName](../hosting/iclrstrongname-interface.md) arabirimine bakın.</span><span class="sxs-lookup"><span data-stu-id="639d3-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="639d3-110">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="639d3-111">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="639d3-112">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-113">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="639d3-114">Belirtilen karma algoritmasını kullanarak, Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="639d3-115">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-116">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="639d3-117">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="639d3-118">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-119">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="639d3-120">Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="639d3-121">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-122">GetHashFromFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="639d3-123">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="639d3-124">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-125">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="639d3-126">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="639d3-127">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-128">StrongNameCompareAssemblies İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="639d3-129">İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="639d3-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="639d3-130">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-131">StrongNameErrorInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="639d3-132">Tanımlayıcı ad işlevlerinden biri tarafından oluşturulan son hata kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="639d3-133">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="639d3-134">[StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi bir tanımlayıcı ad işlevine daha önceki bir çağrı ile ayrılmış belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="639d3-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="639d3-135">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-136">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="639d3-137">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="639d3-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="639d3-138">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-139">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="639d3-140">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="639d3-141">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-142">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="639d3-143">Özel/ortak anahtar çiftinden ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="639d3-144">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-145">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="639d3-146">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="639d3-147">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-148">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="639d3-149">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="639d3-149">Deletes the specified key container.</span></span> <span data-ttu-id="639d3-150">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-151">StrongNameKeyGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="639d3-152">Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="639d3-153">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-154">StrongNameKeyGenEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="639d3-155">Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="639d3-156">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-157">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="639d3-158">Bir kapsayıcıya ortak/özel anahtar çifti aktarır.</span><span class="sxs-lookup"><span data-stu-id="639d3-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="639d3-159">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-160">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="639d3-161">Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="639d3-162">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-163">StrongNameSignatureGenerationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="639d3-164">Belirtilen bayrakları temel alarak, belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="639d3-165">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-166">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="639d3-167">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="639d3-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="639d3-168">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-169">StrongNameSignatureVerification İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="639d3-170">Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="639d3-171">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-172">StrongNameSignatureVerificationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="639d3-173">Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="639d3-174">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-175">StrongNameSignatureVerificationFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="639d3-176">Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="639d3-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="639d3-177">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-178">StrongNameTokenFromAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="639d3-179">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="639d3-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="639d3-180">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-181">StrongNameTokenFromAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="639d3-182">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve ortak anahtarı döndürür.</span><span class="sxs-lookup"><span data-stu-id="639d3-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="639d3-183">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-184">StrongNameTokenFromPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="639d3-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="639d3-185">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="639d3-185">Gets a token representing a public key.</span></span> <span data-ttu-id="639d3-186">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="639d3-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="639d3-187">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="639d3-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="639d3-188">İkili biçimdeki ortak/özel anahtar çiftinin ortak anahtarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="639d3-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639d3-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="639d3-189">See also</span></span>

- [<span data-ttu-id="639d3-190">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="639d3-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="639d3-191">Yönetilmeyen API başvurusu</span><span class="sxs-lookup"><span data-stu-id="639d3-191">Unmanaged API Reference</span></span>](../index.md)
