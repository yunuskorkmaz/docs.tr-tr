---
title: 'Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: e67a80fa8f9a088f0eefe2dd2eeaa983e0a5a2c3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590044"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="d120d-102">Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="d120d-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="d120d-103">Bu örnek, "ad" ve "Isabella" değer çiftini geçerli kullanıcının kayıt defterine, "adlar" anahtarı altında ekler.</span><span class="sxs-lookup"><span data-stu-id="d120d-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="d120d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d120d-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d120d-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d120d-105">Compiling the Code</span></span>  
  
- <span data-ttu-id="d120d-106">Kodu kopyalayın ve konsol uygulamasının `Main` yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="d120d-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="d120d-107">Parametresini, `Names` doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünün altında bulunan bir anahtarın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d120d-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="d120d-108">`Name` Parametresini doğrudan Names düğümünün altında bulunan bir değerin adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d120d-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d120d-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d120d-109">Robust Programming</span></span>  
 <span data-ttu-id="d120d-110">Anahtarınız için uygun bir konum bulmak üzere kayıt defteri yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="d120d-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="d120d-111">Örneğin, geçerli kullanıcının yazılım anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d120d-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="d120d-112">Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d120d-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="d120d-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d120d-113">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="d120d-114">Anahtarın adı null.</span><span class="sxs-lookup"><span data-stu-id="d120d-114">The name of the key is null.</span></span>  
  
- <span data-ttu-id="d120d-115">Kullanıcının kayıt defteri anahtarları oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="d120d-115">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="d120d-116">Anahtar adı 255 karakterlik sınırı aşıyor.</span><span class="sxs-lookup"><span data-stu-id="d120d-116">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="d120d-117">Anahtar kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="d120d-117">The key is closed.</span></span>  
  
- <span data-ttu-id="d120d-118">Kayıt defteri anahtarı salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="d120d-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d120d-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d120d-119">.NET Framework Security</span></span>  
 <span data-ttu-id="d120d-120">`Microsoft.Win32.Registry.CurrentUser` Yerel`Microsoft.Win32.Registry.LocalMachine`bilgisayar yerine, Kullanıcı klasörüne veri yazmak daha güvenlidir —.</span><span class="sxs-lookup"><span data-stu-id="d120d-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="d120d-121">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d120d-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="d120d-122">Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d120d-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="d120d-123">Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d120d-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="d120d-124">Bunu engellemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="d120d-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="d120d-125">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="d120d-125">method.</span></span> <span data-ttu-id="d120d-126">Anahtar zaten mevcut değilse null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d120d-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="d120d-127">Kayıt defteri anahtarı erişim denetim listeleriyle (ACL) korunuyorsa bile, parolalar gibi gizli dizileri, kayıt defterinde düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="d120d-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d120d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d120d-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="d120d-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d120d-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d120d-130">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d120d-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="d120d-131">İle kayıt defterinden okuma, yazma ve silmeC#</span><span class="sxs-lookup"><span data-stu-id="d120d-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
