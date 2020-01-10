---
title: Kayıt defteri- C# programlama kılavuzunda anahtar oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 16974db950a3a460416cfb917147439707e1d007
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635450"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="cf903-102">Kayıt defterinde anahtar oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cf903-102">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="cf903-103">Bu örnek, "ad" ve "Isabella" değer çiftini geçerli kullanıcının kayıt defterine, "adlar" anahtarı altında ekler.</span><span class="sxs-lookup"><span data-stu-id="cf903-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf903-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf903-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cf903-105">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="cf903-105">Compiling the Code</span></span>  
  
- <span data-ttu-id="cf903-106">Kodu kopyalayın ve bir konsol uygulamasının `Main` yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf903-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="cf903-107">`Names` parametresini, doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünün altında bulunan bir anahtarın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cf903-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="cf903-108">`Name` parametresini doğrudan adlar düğümünün altında bulunan bir değerin adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cf903-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cf903-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="cf903-109">Robust Programming</span></span>  
 <span data-ttu-id="cf903-110">Anahtarınız için uygun bir konum bulmak üzere kayıt defteri yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="cf903-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="cf903-111">Örneğin, geçerli kullanıcının yazılım anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf903-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="cf903-112">Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf903-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="cf903-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="cf903-113">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="cf903-114">Anahtarın adı null.</span><span class="sxs-lookup"><span data-stu-id="cf903-114">The name of the key is null.</span></span>  
  
- <span data-ttu-id="cf903-115">Kullanıcının kayıt defteri anahtarları oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="cf903-115">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="cf903-116">Anahtar adı 255 karakterlik sınırı aşıyor.</span><span class="sxs-lookup"><span data-stu-id="cf903-116">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="cf903-117">Anahtar kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf903-117">The key is closed.</span></span>  
  
- <span data-ttu-id="cf903-118">Kayıt defteri anahtarı salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="cf903-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cf903-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cf903-119">.NET Framework Security</span></span>  
 <span data-ttu-id="cf903-120">Kullanıcı klasörüne veri yazmak daha güvenlidir — yerel bilgisayar yerine `Microsoft.Win32.Registry.CurrentUser` (`Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="cf903-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="cf903-121">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf903-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="cf903-122">Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf903-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="cf903-123">Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf903-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="cf903-124">Bunu engellemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="cf903-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="cf903-125">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="cf903-125">method.</span></span> <span data-ttu-id="cf903-126">Anahtar zaten mevcut değilse null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf903-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="cf903-127">Kayıt defteri anahtarı erişim denetim listeleriyle (ACL) korunuyorsa bile, parolalar gibi gizli dizileri, kayıt defterinde düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="cf903-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf903-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf903-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="cf903-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cf903-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cf903-130">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cf903-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="cf903-131">İle kayıt defterinden okuma, yazma ve silmeC#</span><span class="sxs-lookup"><span data-stu-id="cf903-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
