---
title: 'Nasıl yapılır: Veri Korumayı Kullanma'
description: .NET 'teki veri koruma API 'sine (DPAPI) erişerek veri koruma 'yı nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598599"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="d1fae-103">Nasıl yapılır: Veri Korumayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="d1fae-103">How to: Use Data Protection</span></span>
<span data-ttu-id="d1fae-104">.NET Framework, veri koruma API 'sine (DPAPI) erişim sağlar. Bu, geçerli kullanıcı hesabındaki veya bilgisayardaki bilgileri kullanarak verileri şifrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1fae-104">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="d1fae-105">DPAPI 'yı kullandığınızda, bir şifreleme anahtarını açıkça oluşturma ve depolama konusunda zor olan sorunu gidereolursunuz.</span><span class="sxs-lookup"><span data-stu-id="d1fae-105">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="d1fae-106"><xref:System.Security.Cryptography.ProtectedMemory>Bellek içi bayt dizisini şifrelemek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1fae-106">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="d1fae-107">Bu işlev, Microsoft Windows XP ve sonraki işletim sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1fae-107">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="d1fae-108">Geçerli işlem tarafından şifrelenmiş belleğin, tüm işlemlerle veya aynı kullanıcı bağlamından yalnızca geçerli işlem tarafından çözülemediğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1fae-108">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="d1fae-109"><xref:System.Security.Cryptography.MemoryProtectionScope>Seçeneklerin ayrıntılı açıklaması için bkz. sabit listesi <xref:System.Security.Cryptography.ProtectedMemory> .</span><span class="sxs-lookup"><span data-stu-id="d1fae-109">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="d1fae-110">Bir <xref:System.Security.Cryptography.ProtectedData> bayt dizisinin kopyasını şifrelemek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1fae-110">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="d1fae-111">Bu işlev, Microsoft Windows 2000 ve sonraki işletim sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1fae-111">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="d1fae-112">Geçerli Kullanıcı hesabı tarafından şifrelenen verilerin yalnızca aynı kullanıcı hesabı tarafından çözülemediğini belirtebilir veya geçerli kullanıcı hesabı tarafından şifrelenen verilerin, bilgisayardaki herhangi bir hesap tarafından çözülebilecek olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1fae-112">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="d1fae-113"><xref:System.Security.Cryptography.DataProtectionScope>Seçeneklerin ayrıntılı açıklaması için bkz. sabit listesi <xref:System.Security.Cryptography.ProtectedData> .</span><span class="sxs-lookup"><span data-stu-id="d1fae-113">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="d1fae-114">Veri koruma kullanarak bellek içi verileri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="d1fae-114">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="d1fae-115"><xref:System.Security.Cryptography.ProtectedMemory.Protect%2A>Şifrelemek, entropi ve bellek koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1fae-115">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="d1fae-116">Veri koruma kullanarak bellek içi verilerin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="d1fae-116">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="d1fae-117"><xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A>Şifre çözme ve bellek koruma kapsamının bir bayt dizisini geçirirken statik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1fae-117">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="d1fae-118">Veri koruma kullanarak bir dosya veya akışa veri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="d1fae-118">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="d1fae-119">Rastgele entropi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d1fae-119">Create random entropy.</span></span>  
  
2. <span data-ttu-id="d1fae-120"><xref:System.Security.Cryptography.ProtectedData.Protect%2A>Şifrelemek, entropi ve veri koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1fae-120">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="d1fae-121">Şifrelenmiş verileri bir dosyaya veya akışa yazın.</span><span class="sxs-lookup"><span data-stu-id="d1fae-121">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="d1fae-122">Veri koruma kullanarak bir dosya veya akıştan verilerin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="d1fae-122">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="d1fae-123">Şifrelenen verileri bir dosyadan veya akıştan okuyun.</span><span class="sxs-lookup"><span data-stu-id="d1fae-123">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="d1fae-124"><xref:System.Security.Cryptography.ProtectedData.Unprotect%2A>Şifre çözme ve veri koruma kapsamı için bir bayt dizisi geçirirken statik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1fae-124">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1fae-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1fae-125">Example</span></span>  
 <span data-ttu-id="d1fae-126">Aşağıdaki kod örneği, iki şifreleme ve şifre çözme biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1fae-126">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="d1fae-127">İlk olarak, kod örneği, bellek içi bayt dizisinin şifresini şifreler ve şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="d1fae-127">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="d1fae-128">Ardından, kod örneği bir bayt dizisinin kopyasını şifreler, bir dosyaya kaydeder, verileri dosyadan geri yükler ve sonra verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="d1fae-128">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="d1fae-129">Örnek, özgün verileri, şifrelenen verileri ve şifresi çözülen verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d1fae-129">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1fae-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d1fae-130">Compiling the Code</span></span>  
  
- <span data-ttu-id="d1fae-131">Öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="d1fae-131">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="d1fae-132">,, <xref:System> <xref:System.IO> <xref:System.Security.Cryptography> Ve <xref:System.Text> ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1fae-132">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1fae-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1fae-133">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
