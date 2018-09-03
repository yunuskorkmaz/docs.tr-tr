---
title: 'Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: f2b2cfcb09dc0c8c4d65b64f5de55c0b72746457
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480614"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="1f187-102">Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="1f187-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="1f187-103">Bu örnek "Name" ve "Isabella" değer çiftini geçerli kullanıcının kayıt defterine "Names" anahtarı altına ekler.</span><span class="sxs-lookup"><span data-stu-id="1f187-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f187-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f187-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f187-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1f187-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1f187-106">Kodu kopyalayın ve yapıştırın `Main` konsol uygulamasının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f187-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="1f187-107">Değiştirin `Names` parametresini doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünde bulunan bir anahtarın adıyla.</span><span class="sxs-lookup"><span data-stu-id="1f187-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="1f187-108">Değiştirin `Name` parametresini doğrudan adlar düğümünde bulunan bir değerin adıyla.</span><span class="sxs-lookup"><span data-stu-id="1f187-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1f187-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1f187-109">Robust Programming</span></span>  
 <span data-ttu-id="1f187-110">Anahtarınız için uygun bir konum bulmak üzere kayıt yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="1f187-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="1f187-111">Örneğin, geçerli kullanıcı için yazılım anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f187-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="1f187-112">Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f187-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="1f187-113">Aşağıdaki koşullar özel bir duruma neden:</span><span class="sxs-lookup"><span data-stu-id="1f187-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="1f187-114">Anahtar adı null.</span><span class="sxs-lookup"><span data-stu-id="1f187-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="1f187-115">Kullanıcının kayıt defteri anahtarlarını oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="1f187-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="1f187-116">Anahtar adı 255 karakter sınırını aşıyor.</span><span class="sxs-lookup"><span data-stu-id="1f187-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="1f187-117">Anahtar kapalı.</span><span class="sxs-lookup"><span data-stu-id="1f187-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="1f187-118">Kayıt defteri anahtarı salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="1f187-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1f187-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1f187-119">.NET Framework Security</span></span>  
 <span data-ttu-id="1f187-120">Verilerin kullanıcı klasörüne yazılması daha güvenlidir; `Microsoft.Win32.Registry.CurrentUser` — yerine yerel bilgisayarda — `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="1f187-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="1f187-121">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f187-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="1f187-122">Başka bir işlem, belki de kötü amaçlı bir değeri önceden oluşturmuş olabilir ve erişmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f187-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="1f187-123">Kayıt defteri değerine veri koyduğunuzda, veriler başka bir işlem için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f187-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="1f187-124">Bunu önlemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="1f187-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="1f187-125">yöntem.</span><span class="sxs-lookup"><span data-stu-id="1f187-125">method.</span></span> <span data-ttu-id="1f187-126">Anahtar zaten mevcut değilse null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f187-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="1f187-127">Kayıt defteri anahtarı erişim denetim listeleri (ACL) korunuyor olsa bile kayıt defterinde düz metin parolalar gibi gizli dizileri depolamak için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="1f187-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f187-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f187-128">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="1f187-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1f187-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1f187-130">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1f187-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="1f187-131">Okuma, yazma ve C# ile kayıt silme</span><span class="sxs-lookup"><span data-stu-id="1f187-131">Read, write and delete from the registry with C#</span></span>](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
