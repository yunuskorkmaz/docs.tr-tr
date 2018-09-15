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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b043c5a2173cff9eb82497f6d4ee8b7c0aa3f14c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45641644"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="ee02e-102">Nasıl yapılır: Veri Korumayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="ee02e-102">How to: Use Data Protection</span></span>
<span data-ttu-id="ee02e-103">.NET Framework veri koruma API'si (geçerli kullanıcı hesabı veya bilgisayar bilgileri kullanarak verileri şifreleme olanak tanıyan DPAPI), erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee02e-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="ee02e-104">DPAPI kullandığınızda, açıkça oluşturma ve bir şifreleme anahtarı depolamak zor bir sorun çıkmıştır.</span><span class="sxs-lookup"><span data-stu-id="ee02e-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="ee02e-105">Kullanım <xref:System.Security.Cryptography.ProtectedMemory> bellek içi bir bayt dizisi şifrelemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ee02e-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="ee02e-106">Bu işlev, Microsoft Windows XP ve üstü işletim sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee02e-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="ee02e-107">Geçerli tarafından şifrelenmiş belleğin belirtebilirsiniz işlem şifresi yalnızca, tüm işlemler tarafından ya da aynı kullanıcı bağlamından geçerli işlem.</span><span class="sxs-lookup"><span data-stu-id="ee02e-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="ee02e-108">Bkz: <xref:System.Security.Cryptography.MemoryProtectionScope> numaralandırma ayrıntılı bir açıklaması için <xref:System.Security.Cryptography.ProtectedMemory> seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="ee02e-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="ee02e-109">Kullanım <xref:System.Security.Cryptography.ProtectedData> Bayt dizisine bir kopyasını şifrelemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ee02e-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="ee02e-110">Bu işlev, Microsoft Windows 2000 ve sonraki işletim sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee02e-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="ee02e-111">Geçerli kullanıcı hesabı tarafından şifrelenmiş verilerin yalnızca aynı kullanıcı hesabı tarafından şifresi çözülemez veya geçerli kullanıcı hesabı tarafından şifrelenmiş verilere bilgisayarda herhangi bir hesabı tarafından çözülecek şekilde belirtebilirsiniz belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee02e-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="ee02e-112">Bkz: <xref:System.Security.Cryptography.DataProtectionScope> numaralandırma ayrıntılı bir açıklaması için <xref:System.Security.Cryptography.ProtectedData> seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="ee02e-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="ee02e-113">Veri korumayı kullanarak bellek içi verileri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="ee02e-113">To encrypt in-memory data using data protection</span></span>  
  
1.  <span data-ttu-id="ee02e-114">Statik çağrı <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> şifrelemek için bayt entropi ve bellek koruma kapsamını bir dizi geçirme sırasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee02e-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="ee02e-115">Veri korumayı kullanarak bellek içi verilerin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="ee02e-115">To decrypt in-memory data using data protection</span></span>  
  
1.  <span data-ttu-id="ee02e-116">Statik çağrı <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> şifresini çözmek için bayt ve bellek koruma kapsamını bir dizi geçirme sırasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee02e-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="ee02e-117">Veri korumayı kullanarak akış veya dosyaya verileri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="ee02e-117">To encrypt data to a file or stream using data protection</span></span>  
  
1.  <span data-ttu-id="ee02e-118">Rastgele entropi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ee02e-118">Create random entropy.</span></span>  
  
2.  <span data-ttu-id="ee02e-119">Statik çağrı <xref:System.Security.Cryptography.ProtectedData.Protect%2A> şifrelemek için bayt entropi ve veri koruma kapsamını bir dizi geçirme sırasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee02e-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3.  <span data-ttu-id="ee02e-120">Şifrelenmiş veriler, bir dosya veya akışınıza yazın.</span><span class="sxs-lookup"><span data-stu-id="ee02e-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="ee02e-121">Bir dosyadan verilerin şifresini çözmek veya veri koruması kullanarak akış</span><span class="sxs-lookup"><span data-stu-id="ee02e-121">To decrypt data from a file or stream using data protection</span></span>  
  
1.  <span data-ttu-id="ee02e-122">Şifrelenmiş veriler, bir dosya veya akıştan okuyun.</span><span class="sxs-lookup"><span data-stu-id="ee02e-122">Read the encrypted data from a file or stream.</span></span>  
  
2.  <span data-ttu-id="ee02e-123">Statik çağrı <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> şifresini çözmek için bayt ve verileri koruma kapsamını bir dizi geçirme sırasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee02e-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee02e-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee02e-124">Example</span></span>  
 <span data-ttu-id="ee02e-125">Aşağıdaki kod örneği, iki tür şifreleme ve şifre çözme gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee02e-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="ee02e-126">İlk olarak, kod örneği, şifreler ve daha sonra bir bellek içi bayt dizisi şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="ee02e-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="ee02e-127">Ardından, kod örneği bir bayt dizisinin bir kopyasını şifreler, bir dosyaya kaydeder, verileri dosyadan geri yükler ve ardından verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="ee02e-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="ee02e-128">Örneğin, şifresi çözülmüş veriler özgün veri ve şifrelenmiş verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ee02e-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ee02e-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ee02e-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ee02e-130">Bir başvuru eklemek `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="ee02e-130">Include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="ee02e-131">Dahil <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, ve <xref:System.Text> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ee02e-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee02e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee02e-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>  
- <xref:System.Security.Cryptography.ProtectedData>
