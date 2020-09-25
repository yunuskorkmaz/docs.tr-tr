---
title: Kayıt defteri-C# programlama kılavuzunda anahtar oluşturma
description: Kayıt defterinde anahtar oluşturmayı öğrenin. Bkz. bir kod örneği, yönergeleri derleme ve kullanılabilir ek kaynaklar.
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: c51fa61aa4c501921d5c7ace99a8c5aaf7b29f58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203923"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="bb80e-104">Kayıt defterinde anahtar oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bb80e-104">How to create a key in the registry (C# Programming Guide)</span></span>

<span data-ttu-id="bb80e-105">Bu örnek, "ad" ve "Isabella" değer çiftini geçerli kullanıcının kayıt defterine, "adlar" anahtarı altında ekler.</span><span class="sxs-lookup"><span data-stu-id="bb80e-105">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb80e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb80e-106">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb80e-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bb80e-107">Compiling the Code</span></span>  
  
- <span data-ttu-id="bb80e-108">Kodu kopyalayın ve `Main` konsol uygulamasının yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="bb80e-108">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="bb80e-109">Parametresini, `Names` doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünün altında bulunan bir anahtarın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bb80e-109">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="bb80e-110">`Name`Parametresini doğrudan Names düğümünün altında bulunan bir değerin adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bb80e-110">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bb80e-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="bb80e-111">Robust Programming</span></span>  

 <span data-ttu-id="bb80e-112">Anahtarınız için uygun bir konum bulmak üzere kayıt defteri yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="bb80e-112">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="bb80e-113">Örneğin, geçerli kullanıcının yazılım anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb80e-113">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="bb80e-114">Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bb80e-114">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="bb80e-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="bb80e-115">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="bb80e-116">Anahtarın adı null.</span><span class="sxs-lookup"><span data-stu-id="bb80e-116">The name of the key is null.</span></span>  
  
- <span data-ttu-id="bb80e-117">Kullanıcının kayıt defteri anahtarları oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="bb80e-117">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="bb80e-118">Anahtar adı 255 karakterlik sınırı aşıyor.</span><span class="sxs-lookup"><span data-stu-id="bb80e-118">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="bb80e-119">Anahtar kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb80e-119">The key is closed.</span></span>  
  
- <span data-ttu-id="bb80e-120">Kayıt defteri anahtarı salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="bb80e-120">The registry key is read-only.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="bb80e-121">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="bb80e-121">.NET Security</span></span>  

 <span data-ttu-id="bb80e-122">Yerel bilgisayar yerine, Kullanıcı klasörüne veri yazmak daha güvenlidir — `Microsoft.Win32.Registry.CurrentUser` `Microsoft.Win32.Registry.LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="bb80e-122">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="bb80e-123">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb80e-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="bb80e-124">Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb80e-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="bb80e-125">Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb80e-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="bb80e-126">Bunu engellemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="bb80e-126">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="bb80e-127">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="bb80e-127">method.</span></span> <span data-ttu-id="bb80e-128">Anahtar zaten mevcut değilse null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb80e-128">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="bb80e-129">Kayıt defteri anahtarı erişim denetim listeleriyle (ACL) korunuyorsa bile, parolalar gibi gizli dizileri, kayıt defterinde düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="bb80e-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb80e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb80e-130">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="bb80e-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb80e-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bb80e-132">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bb80e-132">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="bb80e-133">C ile kayıt defterinden okuma, yazma ve silme #</span><span class="sxs-lookup"><span data-stu-id="bb80e-133">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
