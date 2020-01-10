---
title: 'Nasıl yapılır: Veri Korumayı Kullanma'
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
ms.openlocfilehash: 0efd677f11189b28b8efc184c04b30a047ab942b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706038"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="97fb4-102">Nasıl yapılır: Veri Korumayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="97fb4-102">How to: Use Data Protection</span></span>
<span data-ttu-id="97fb4-103">.NET Framework, veri koruma API 'sine (DPAPI) erişim sağlar. Bu, geçerli kullanıcı hesabındaki veya bilgisayardaki bilgileri kullanarak verileri şifrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="97fb4-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="97fb4-104">DPAPI 'yı kullandığınızda, bir şifreleme anahtarını açıkça oluşturma ve depolama konusunda zor olan sorunu gidereolursunuz.</span><span class="sxs-lookup"><span data-stu-id="97fb4-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="97fb4-105">Bellek içi bayt dizisini şifrelemek için <xref:System.Security.Cryptography.ProtectedMemory> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fb4-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="97fb4-106">Bu işlev, Microsoft Windows XP ve sonraki işletim sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97fb4-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="97fb4-107">Geçerli işlem tarafından şifrelenmiş belleğin, tüm işlemlerle veya aynı kullanıcı bağlamından yalnızca geçerli işlem tarafından çözülemediğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fb4-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="97fb4-108"><xref:System.Security.Cryptography.ProtectedMemory> seçeneklerinin ayrıntılı bir açıklaması için bkz. <xref:System.Security.Cryptography.MemoryProtectionScope> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="97fb4-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="97fb4-109">Bir bayt dizisinin bir kopyasını şifrelemek için <xref:System.Security.Cryptography.ProtectedData> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fb4-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="97fb4-110">Bu işlev, Microsoft Windows 2000 ve sonraki işletim sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97fb4-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="97fb4-111">Geçerli Kullanıcı hesabı tarafından şifrelenen verilerin yalnızca aynı kullanıcı hesabı tarafından çözülemediğini belirtebilir veya geçerli kullanıcı hesabı tarafından şifrelenen verilerin, bilgisayardaki herhangi bir hesap tarafından çözülebilecek olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fb4-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="97fb4-112"><xref:System.Security.Cryptography.ProtectedData> seçeneklerinin ayrıntılı bir açıklaması için bkz. <xref:System.Security.Cryptography.DataProtectionScope> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="97fb4-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="97fb4-113">Veri koruma kullanarak bellek içi verileri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="97fb4-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="97fb4-114">Şifrelemek, entropi ve bellek koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97fb4-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="97fb4-115">Veri koruma kullanarak bellek içi verilerin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="97fb4-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="97fb4-116">Şifre çözme ve bellek koruma kapsamının bir bayt dizisini geçirirken statik <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97fb4-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="97fb4-117">Veri koruma kullanarak bir dosya veya akışa veri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="97fb4-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="97fb4-118">Rastgele entropi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97fb4-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="97fb4-119">Şifrelemek, entropi ve veri koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik <xref:System.Security.Cryptography.ProtectedData.Protect%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97fb4-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="97fb4-120">Şifrelenmiş verileri bir dosyaya veya akışa yazın.</span><span class="sxs-lookup"><span data-stu-id="97fb4-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="97fb4-121">Veri koruma kullanarak bir dosya veya akıştan verilerin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="97fb4-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="97fb4-122">Şifrelenen verileri bir dosyadan veya akıştan okuyun.</span><span class="sxs-lookup"><span data-stu-id="97fb4-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="97fb4-123">Şifre çözme ve veri koruma kapsamı için bir bayt dizisi geçirirken statik <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97fb4-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97fb4-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="97fb4-124">Example</span></span>  
 <span data-ttu-id="97fb4-125">Aşağıdaki kod örneği, iki şifreleme ve şifre çözme biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="97fb4-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="97fb4-126">İlk olarak, kod örneği, bellek içi bayt dizisinin şifresini şifreler ve şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="97fb4-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="97fb4-127">Ardından, kod örneği bir bayt dizisinin kopyasını şifreler, bir dosyaya kaydeder, verileri dosyadan geri yükler ve sonra verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="97fb4-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="97fb4-128">Örnek, özgün verileri, şifrelenen verileri ve şifresi çözülen verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="97fb4-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="97fb4-129">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="97fb4-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="97fb4-130">`System.Security.dll`bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97fb4-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="97fb4-131"><xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>ve <xref:System.Text> ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97fb4-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fb4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97fb4-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
