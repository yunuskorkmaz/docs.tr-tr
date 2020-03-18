---
title: Kayıt defterinde anahtar oluşturma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 16974db950a3a460416cfb917147439707e1d007
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635450"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="da7b4-102">Kayıt defterinde anahtar oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="da7b4-102">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="da7b4-103">Bu örnek, geçerli kullanıcının kayıt defterine "Adlar" anahtarı altında "Ad" ve "Isabella" değer çiftini ekler.</span><span class="sxs-lookup"><span data-stu-id="da7b4-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="da7b4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="da7b4-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da7b4-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="da7b4-105">Compiling the Code</span></span>  
  
- <span data-ttu-id="da7b4-106">Kodu kopyalayın ve konsol `Main` uygulamasının yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="da7b4-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="da7b4-107">Parametreyi, `Names` doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünün altında bulunan bir anahtarın adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="da7b4-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="da7b4-108">Parametreyi, `Name` Doğrudan Ad düğümünün altında bulunan bir değerin adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="da7b4-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="da7b4-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="da7b4-109">Robust Programming</span></span>  
 <span data-ttu-id="da7b4-110">Anahtarınız için uygun bir yer bulmak için kayıt defteri yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="da7b4-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="da7b4-111">Örneğin, geçerli kullanıcının Yazılım anahtarını açıp şirketinizin adını içeren bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da7b4-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="da7b4-112">Ardından şirket defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="da7b4-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="da7b4-113">Aşağıdaki koşullar bir özel durum neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="da7b4-113">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="da7b4-114">Anahtarın adı geçersiz.</span><span class="sxs-lookup"><span data-stu-id="da7b4-114">The name of the key is null.</span></span>  
  
- <span data-ttu-id="da7b4-115">Kullanıcının kayıt defteri anahtarları oluşturma izinleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="da7b4-115">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="da7b4-116">Anahtar adı 255 karakter sınırını aşıyor.</span><span class="sxs-lookup"><span data-stu-id="da7b4-116">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="da7b4-117">Anahtar kapalı.</span><span class="sxs-lookup"><span data-stu-id="da7b4-117">The key is closed.</span></span>  
  
- <span data-ttu-id="da7b4-118">Kayıt defteri anahtarı salt okunur.</span><span class="sxs-lookup"><span data-stu-id="da7b4-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="da7b4-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="da7b4-119">.NET Framework Security</span></span>  
 <span data-ttu-id="da7b4-120">Yerel bilgisayara değil, `Microsoft.Win32.Registry.CurrentUser` kullanıcı klasörüne veri yazmak daha güvenlidir. `Microsoft.Win32.Registry.LocalMachine`</span><span class="sxs-lookup"><span data-stu-id="da7b4-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="da7b4-121">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapacağınız gerektiğine karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da7b4-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="da7b4-122">Başka bir işlem, belki de kötü niyetli bir, zaten değer yarattı ve ona erişimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="da7b4-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="da7b4-123">Verileri kayıt defteri değerine koyduğunuzda, veriler diğer işlem için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da7b4-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="da7b4-124">Bunu önlemek için, kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="da7b4-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="da7b4-125">Yöntem.</span><span class="sxs-lookup"><span data-stu-id="da7b4-125">method.</span></span> <span data-ttu-id="da7b4-126">Anahtar zaten yoksa null döndürür.</span><span class="sxs-lookup"><span data-stu-id="da7b4-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="da7b4-127">Kayıt defteri anahtarı erişim denetim listeleri (ACL) tarafından korunsa bile, parolalar gibi sırları kayıt defterinde düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="da7b4-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7b4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da7b4-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="da7b4-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="da7b4-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="da7b4-130">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="da7b4-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="da7b4-131">C ile kayıt defterinden okuma, yazma ve silme #</span><span class="sxs-lookup"><span data-stu-id="da7b4-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
