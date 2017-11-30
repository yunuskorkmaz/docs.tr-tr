---
title: "Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6cc79a8a914d3ef5b7c496db4dc0d2b3eb17768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="24092-102">Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="24092-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="24092-103">Bu örnek, geçerli kullanıcının kayıt defteri anahtarı "Adı" altında "Name" ve "Isabella" değer çifti ekler.</span><span class="sxs-lookup"><span data-stu-id="24092-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="24092-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="24092-104">Example</span></span>  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24092-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="24092-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="24092-106">Kodu kopyalayın ve yapıştırın `Main` bir konsol uygulaması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="24092-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="24092-107">Değiştir `Names` doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünde mevcut bir anahtarı adlı parametre.</span><span class="sxs-lookup"><span data-stu-id="24092-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="24092-108">Değiştir `Name` doğrudan adları düğümü altında varolan bir değer adlı parametre.</span><span class="sxs-lookup"><span data-stu-id="24092-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="24092-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="24092-109">Robust Programming</span></span>  
 <span data-ttu-id="24092-110">Anahtarınız için uygun bir konum bulmak için kayıt defteri yapısı inceleyin.</span><span class="sxs-lookup"><span data-stu-id="24092-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="24092-111">Örneğin, geçerli kullanıcının yazılım anahtarı açın ve şirketinizin adı ile bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24092-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="24092-112">Ardından, şirketinizin anahtarına kayıt defteri değerlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24092-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="24092-113">Aşağıdaki koşullar, bir özel durum neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="24092-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="24092-114">Anahtar adı null.</span><span class="sxs-lookup"><span data-stu-id="24092-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="24092-115">Kullanıcının kayıt defteri anahtarları oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="24092-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="24092-116">Anahtar adı 255 karakter sınırını aşıyor.</span><span class="sxs-lookup"><span data-stu-id="24092-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="24092-117">Anahtar kapalı.</span><span class="sxs-lookup"><span data-stu-id="24092-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="24092-118">Kayıt defteri anahtarı salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="24092-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="24092-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="24092-119">.NET Framework Security</span></span>  
 <span data-ttu-id="24092-120">Kullanıcı klasörüne veri yazmak için daha güvenlidir — `Microsoft.Win32.Registry.CurrentUser` — yerine yerel bilgisayarda — `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="24092-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="24092-121">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24092-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="24092-122">Başka bir işlem, belki de kötü amaçlı bir değer önceden oluşturduğunuz ve buna erişiminiz.</span><span class="sxs-lookup"><span data-stu-id="24092-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="24092-123">Kayıt defteri değerindeki veri geçirdiğinizde, verileri başka bir işlem mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="24092-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="24092-124">Bunu önlemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="24092-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="24092-125">yöntem.</span><span class="sxs-lookup"><span data-stu-id="24092-125">method.</span></span> <span data-ttu-id="24092-126">Anahtar zaten mevcut değilse null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="24092-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="24092-127">Kayıt defteri anahtarı erişim denetim listeleri (ACL) tarafından korunan olsa bile düz metin olarak kayıt defterinde parolalar gibi gizli depolamak için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="24092-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24092-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24092-128">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="24092-129">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24092-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="24092-130">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="24092-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="24092-131">Okuma, yazma ve C# ile kayıt defterinden silme</span><span class="sxs-lookup"><span data-stu-id="24092-131">Read, write and delete from the registry with C#</span></span>](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
