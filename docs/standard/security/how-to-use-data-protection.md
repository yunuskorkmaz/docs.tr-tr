---
title: 'Nasıl yapılır: Veri Korumayı Kullanma'
description: .NET 'teki veri koruma API 'sine (DPAPI) erişerek veri koruma 'yı nasıl kullanacağınızı öğrenin.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: 263a07ddf357734e819fffdd41cdff60657adf15
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557066"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="49577-103">Nasıl yapılır: Veri Korumayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="49577-103">How to: Use Data Protection</span></span>

> [!NOTE]
> <span data-ttu-id="49577-104">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="49577-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="49577-105">ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="49577-105">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="49577-106">.NET, veri koruma API 'sine (DPAPI) erişim sağlar. Bu, geçerli kullanıcı hesabındaki veya bilgisayardaki bilgileri kullanarak verileri şifrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="49577-106">.NET provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="49577-107">DPAPI 'yı kullandığınızda, bir şifreleme anahtarını açıkça oluşturma ve depolama konusunda zor olan sorunu gidereolursunuz.</span><span class="sxs-lookup"><span data-stu-id="49577-107">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
<span data-ttu-id="49577-108">Bir <xref:System.Security.Cryptography.ProtectedData> bayt dizisinin kopyasını şifrelemek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="49577-108">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="49577-109">Bu işlevsellik .NET Framework, .NET Core ve .NET 5 ' te kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="49577-109">This functionality is available in .NET Framework, .NET Core, and .NET 5.</span></span>  <span data-ttu-id="49577-110">Geçerli Kullanıcı hesabı tarafından şifrelenen verilerin yalnızca aynı kullanıcı hesabı tarafından çözülemediğini belirtebilir veya geçerli kullanıcı hesabı tarafından şifrelenen verilerin, bilgisayardaki herhangi bir hesap tarafından çözülebilecek olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49577-110">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="49577-111"><xref:System.Security.Cryptography.DataProtectionScope>Seçeneklerin ayrıntılı açıklaması için bkz. sabit listesi <xref:System.Security.Cryptography.ProtectedData> .</span><span class="sxs-lookup"><span data-stu-id="49577-111">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="49577-112">Veri koruma kullanarak bir dosya veya akışa veri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="49577-112">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="49577-113">Rastgele entropi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49577-113">Create random entropy.</span></span>  
  
2. <span data-ttu-id="49577-114"><xref:System.Security.Cryptography.ProtectedData.Protect%2A>Şifrelemek, entropi ve veri koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="49577-114">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="49577-115">Şifrelenmiş verileri bir dosyaya veya akışa yazın.</span><span class="sxs-lookup"><span data-stu-id="49577-115">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="49577-116">Veri koruma kullanarak bir dosya veya akıştan verilerin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="49577-116">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="49577-117">Şifrelenen verileri bir dosyadan veya akıştan okuyun.</span><span class="sxs-lookup"><span data-stu-id="49577-117">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="49577-118"><xref:System.Security.Cryptography.ProtectedData.Unprotect%2A>Şifre çözme ve veri koruma kapsamı için bir bayt dizisi geçirirken statik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="49577-118">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49577-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="49577-119">Example</span></span>

<span data-ttu-id="49577-120">Aşağıdaki kod örneği, iki şifreleme ve şifre çözme biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="49577-120">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="49577-121">İlk olarak, kod örneği, bellek içi bayt dizisinin şifresini şifreler ve şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="49577-121">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="49577-122">Ardından, kod örneği bir bayt dizisinin kopyasını şifreler, bir dosyaya kaydeder, verileri dosyadan geri yükler ve sonra verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="49577-122">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="49577-123">Örnek, özgün verileri, şifrelenen verileri ve şifresi çözülen verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="49577-123">The example displays the original data, the encrypted data, and the decrypted data.</span></span>

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49577-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="49577-124">Compiling the Code</span></span>  

<span data-ttu-id="49577-125">Bu örnek, yalnızca .NET Framework ve Windows üzerinde çalışan durumlarda derlenir ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="49577-125">This example compiles and runs only when targeting .NET Framework and running on Windows.</span></span>

- <span data-ttu-id="49577-126">Öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="49577-126">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="49577-127">,, <xref:System> <xref:System.IO> <xref:System.Security.Cryptography> Ve <xref:System.Text> ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="49577-127">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49577-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49577-128">See also</span></span>

- [<span data-ttu-id="49577-129">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="49577-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="49577-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="49577-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="49577-131">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="49577-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [<span data-ttu-id="49577-132">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="49577-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
