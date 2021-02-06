---
description: 'Daha fazla bilgi edinin: tanımlayıcı adlandırma (yönetilmeyen API Başvurusu)'
title: Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 058cc51d8e9eb2ef4a2d0670811aefcd32dafb6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646367"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="93c8d-103">Tanımlayıcı Ad Oluşturma (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="93c8d-103">Strong Naming (Unmanaged API Reference)</span></span>

<span data-ttu-id="93c8d-104">Güçlü adlandırma API 'SI, bir istemcinin derlemeler için tanımlayıcı ad imzalamayı yönetmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="93c8d-104">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="93c8d-105">Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak bir anahtar şifrelemesi ekler.</span><span class="sxs-lookup"><span data-stu-id="93c8d-105">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="93c8d-106">Tanımlayıcı ad imzalama, ad benzersizliği doğrulamaya yardımcı olur, ad yanıltmasını önler ve bir başvuru çözüldüğünde çağıranlar benzersiz bir kimlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="93c8d-106">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="93c8d-107">Ancak, tanımlayıcı bir adla ilişkili güven düzeyi yoktur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-107">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93c8d-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="93c8d-108">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93c8d-109">Bu işlevlerin tümü .NET Framework 4 ' den itibaren kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-109">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="93c8d-110">Önerilen alternatifler için [ICLRStrongName](../hosting/iclrstrongname-interface.md) arabirimine bakın.</span><span class="sxs-lookup"><span data-stu-id="93c8d-110">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="93c8d-111">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-111">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="93c8d-112">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-112">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="93c8d-113">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-113">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-114">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-114">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="93c8d-115">Belirtilen karma algoritmasını kullanarak, Unicode dizesi olarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-115">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="93c8d-116">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-116">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-117">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-117">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="93c8d-118">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-118">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="93c8d-119">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-119">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-120">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-120">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="93c8d-121">Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-121">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="93c8d-122">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-122">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-123">GetHashFromFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-123">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="93c8d-124">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-124">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="93c8d-125">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-125">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-126">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-126">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="93c8d-127">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-127">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="93c8d-128">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-128">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-129">StrongNameCompareAssemblies İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-129">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="93c8d-130">İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="93c8d-130">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="93c8d-131">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-131">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-132">StrongNameErrorInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-132">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="93c8d-133">Tanımlayıcı ad işlevlerinden biri tarafından oluşturulan son hata kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-133">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="93c8d-134">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-134">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="93c8d-135">[StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi bir tanımlayıcı ad işlevine daha önceki bir çağrı ile ayrılmış belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-135">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="93c8d-136">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-136">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-137">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-137">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="93c8d-138">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-138">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="93c8d-139">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-139">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-140">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-140">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="93c8d-141">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-141">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="93c8d-142">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-142">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-143">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-143">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="93c8d-144">Özel/ortak anahtar çiftinden ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-144">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="93c8d-145">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-145">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-146">StrongNameHashSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-146">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="93c8d-147">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-147">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="93c8d-148">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-148">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-149">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-149">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="93c8d-150">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="93c8d-150">Deletes the specified key container.</span></span> <span data-ttu-id="93c8d-151">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-151">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-152">StrongNameKeyGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-152">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="93c8d-153">Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-153">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="93c8d-154">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-154">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-155">StrongNameKeyGenEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-155">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="93c8d-156">Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-156">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="93c8d-157">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-157">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-158">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-158">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="93c8d-159">Bir kapsayıcıya ortak/özel anahtar çifti aktarır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-159">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="93c8d-160">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-160">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-161">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-161">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="93c8d-162">Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-162">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="93c8d-163">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-163">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-164">StrongNameSignatureGenerationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-164">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="93c8d-165">Belirtilen bayrakları temel alarak, belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-165">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="93c8d-166">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-166">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-167">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-167">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="93c8d-168">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="93c8d-168">Returns the size of the strong name signature.</span></span> <span data-ttu-id="93c8d-169">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-169">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-170">StrongNameSignatureVerification İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-170">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="93c8d-171">Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-171">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="93c8d-172">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-172">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-173">StrongNameSignatureVerificationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-173">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="93c8d-174">Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-174">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="93c8d-175">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-175">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-176">StrongNameSignatureVerificationFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-176">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="93c8d-177">Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="93c8d-177">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="93c8d-178">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-178">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-179">StrongNameTokenFromAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-179">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="93c8d-180">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93c8d-180">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="93c8d-181">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-181">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-182">StrongNameTokenFromAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-182">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="93c8d-183">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve ortak anahtarı döndürür.</span><span class="sxs-lookup"><span data-stu-id="93c8d-183">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="93c8d-184">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-184">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-185">StrongNameTokenFromPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="93c8d-185">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="93c8d-186">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-186">Gets a token representing a public key.</span></span> <span data-ttu-id="93c8d-187">.NET Framework 4 ile başlayarak kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93c8d-187">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="93c8d-188">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="93c8d-188">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="93c8d-189">İkili biçimdeki ortak/özel anahtar çiftinin ortak anahtarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="93c8d-189">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c8d-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93c8d-190">See also</span></span>

- [<span data-ttu-id="93c8d-191">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93c8d-191">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="93c8d-192">Yönetilmeyen API başvurusu</span><span class="sxs-lookup"><span data-stu-id="93c8d-192">Unmanaged API Reference</span></span>](../index.md)
