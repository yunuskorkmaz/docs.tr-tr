---
title: Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140636"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="cb9f4-102">Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cb9f4-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="cb9f4-103">Güçlü adlandırma API'si, istemcinin derlemeler için güçlü ad imzalamayı yönetmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="cb9f4-104">Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="cb9f4-105">Güçlü ad imzalama, ad benzersizliğini doğrulamaya yardımcı olur, ad sızdırmasını önler ve bir başvuru çözüldüğünde arayanlara benzersiz bir kimlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="cb9f4-106">Ancak, hiçbir güven düzeyi güçlü bir adla ilişkilendirilmez.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb9f4-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cb9f4-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb9f4-108">Bu işlevlerin tümü .NET Framework 4'ten başlayarak amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="cb9f4-109">Önerilen alternatifler için [ICLRStrongName](../hosting/iclrstrongname-interface.md) arabirimine bakın.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="cb9f4-110">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="cb9f4-111">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="cb9f4-112">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-113">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="cb9f4-114">Belirtilen karma algoritmasını kullanarak Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="cb9f4-115">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-116">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="cb9f4-117">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresinde montaj bir karma alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="cb9f4-118">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-119">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="cb9f4-120">Belirtilen dosyanın içeriği üzerinde karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="cb9f4-121">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-122">GetHashFromFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="cb9f4-123">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="cb9f4-124">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-125">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="cb9f4-126">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısıyla dosyanın içeriği üzerinde karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="cb9f4-127">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-128">StrongNameCompareAssemblies İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="cb9f4-129">İki derlemenin yalnızca güçlü ad imzalarına göre farklılık görüp göremeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="cb9f4-130">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-131">StrongNameErrorInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="cb9f4-132">Güçlü ad işlevlerinden biri tarafından yükseltilen son hata kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="cb9f4-133">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="cb9f4-134">[StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi güçlü bir ad işlevine önceki bir çağrıyla ayrılan belleği serbest sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="cb9f4-135">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-136">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="cb9f4-137">Belirtilen arabelleği, belirtilen adreste yürütülebilir dosyanın ikili gösterimiyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="cb9f4-138">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-139">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="cb9f4-140">Belirtilen bellek adresindemontaj görüntüsünün ikili bir temsilini alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="cb9f4-141">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-142">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="cb9f4-143">Ortak anahtarı özel/ortak anahtar çiftinden alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="cb9f4-144">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-145">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="cb9f4-146">Belirtilen karma algoritmasını kullanarak karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="cb9f4-147">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-148">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="cb9f4-149">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-149">Deletes the specified key container.</span></span> <span data-ttu-id="cb9f4-150">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-151">StrongNameKeyGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="cb9f4-152">Güçlü ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="cb9f4-153">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-154">StrongNameKeyGenEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="cb9f4-155">Güçlü ad kullanımı için belirtilen anahtar boyutuna sahip yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="cb9f4-156">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-157">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="cb9f4-158">Bir kapsayıcıya ortak/özel anahtar çifti içe aktun.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="cb9f4-159">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-160">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="cb9f4-161">Belirtilen derleme için güçlü bir ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="cb9f4-162">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-163">StrongNameSignatureGenerationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="cb9f4-164">Belirtilen bayrakları temel alan belirtilen derleme için güçlü bir ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="cb9f4-165">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-166">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="cb9f4-167">Güçlü ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="cb9f4-168">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-169">StrongNameSignatureVerification İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="cb9f4-170">Verilen yolda derleme bildirimi belirtilen bayraklara göre doğrulanmış güçlü bir ad imzası içerip içermediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="cb9f4-171">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-172">StrongNameSignatureVerificationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="cb9f4-173">Verilen yoltaki derleme bildiriminin güçlü bir ad imzası içerip içermediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="cb9f4-174">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-175">StrongNameSignatureVerificationFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="cb9f4-176">Belleğe eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="cb9f4-177">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-178">StrongNameTokenFromAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="cb9f4-179">Belirtilen derleme dosyasından güçlü bir ad belirteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="cb9f4-180">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-181">StrongNameTokenFromAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="cb9f4-182">Belirtilen derleme dosyasından güçlü bir ad belirteci oluşturur ve ortak anahtarı döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="cb9f4-183">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-184">StrongNameTokenFromPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="cb9f4-185">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-185">Gets a token representing a public key.</span></span> <span data-ttu-id="cb9f4-186">.NET Framework 4 ile başlayan amortismana uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="cb9f4-187">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="cb9f4-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="cb9f4-188">Ortak/özel anahtar çiftinin ortak anahtarını ikili biçimde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9f4-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-189">See also</span></span>

- [<span data-ttu-id="cb9f4-190">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb9f4-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="cb9f4-191">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cb9f4-191">Unmanaged API Reference</span></span>](../index.md)
