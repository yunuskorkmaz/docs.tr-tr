---
title: 'Nasıl yapılır: Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: b51a14e5e9c69078330f5b2161f74cff8e4da332
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363454"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="ef5cf-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="ef5cf-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="ef5cf-103">`CreateSubKey` `My.Computer.Registry` Nesnesinin yöntemi bir kayıt defteri anahtarı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="ef5cf-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="ef5cf-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="ef5cf-105">Kayıt defteri anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ef5cf-105">To create a registry key</span></span>

- <span data-ttu-id="ef5cf-106">`CreateSubKey`Anahtar adının yanı sıra anahtarın altına hangi Hive yerleştirileceğini belirterek yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ef5cf-107">Parametre, `Subkey` büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="ef5cf-108">Bu örnek HKEY_CURRENT_USER altında kayıt defteri anahtarı oluşturur `MyTestKey` .</span><span class="sxs-lookup"><span data-stu-id="ef5cf-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="ef5cf-109">Bir kayıt defteri anahtarı oluşturmak ve içinde bir değer ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ef5cf-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="ef5cf-110">`CreateSubkey`Anahtar adının yanı sıra anahtarın altına hangi Hive yerleştirileceğini belirterek yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ef5cf-111">Bu örnek HKEY_CURRENT_USER altında kayıt defteri anahtarı oluşturur `MyTestKey` .</span><span class="sxs-lookup"><span data-stu-id="ef5cf-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="ef5cf-112">Değerini `SetValue` yöntemiyle ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="ef5cf-113">Bu örnek dize değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-113">This example sets the string value.</span></span> <span data-ttu-id="ef5cf-114">"Bu bir test değeridir" için "MyTestKeyValue".</span><span class="sxs-lookup"><span data-stu-id="ef5cf-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="ef5cf-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef5cf-115">Example</span></span>

<span data-ttu-id="ef5cf-116">Bu örnek HKEY_CURRENT_USER altında kayıt defteri anahtarını oluşturur `MyTestKey` ve sonra dize değerini olarak ayarlar `MyTestKeyValue` `This is a test value` .</span><span class="sxs-lookup"><span data-stu-id="ef5cf-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="ef5cf-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ef5cf-117">Robust Programming</span></span>

<span data-ttu-id="ef5cf-118">Anahtarınız için uygun bir konum bulmak üzere kayıt defteri yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="ef5cf-119">Örneğin, geçerli kullanıcının HKEY_CURRENT_USER \Software anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="ef5cf-120">Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="ef5cf-121">Bir Web uygulamasından kayıt defteri okurken, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulamasına ve kimliğe bürünmeye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="ef5cf-122"><xref:Microsoft.Win32.Registry.CurrentUser>Yerel bilgisayar () yerine Kullanıcı klasörüne () veri yazmak daha güvenlidir <xref:Microsoft.Win32.Registry.LocalMachine> .</span><span class="sxs-lookup"><span data-stu-id="ef5cf-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="ef5cf-123">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="ef5cf-124">Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="ef5cf-125">Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="ef5cf-126">Bunu engellemek için <xref:Microsoft.Win32.RegistryKey.GetValue%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="ef5cf-127">`Nothing`Anahtar zaten mevcut değilse döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="ef5cf-128">Kayıt defteri anahtarı ACL 'Ler (Access Control listeleri) tarafından korunsa bile, parolalar gibi gizli dizileri, kayıt defterinde düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="ef5cf-129">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ef5cf-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="ef5cf-130">Anahtarın adı `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="ef5cf-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="ef5cf-131">Kullanıcının kayıt defteri anahtarları oluşturma izni yok ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="ef5cf-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="ef5cf-132">Anahtar adı 255 karakter sınırını ( <xref:System.ArgumentException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="ef5cf-133">Anahtar kapalı ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="ef5cf-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="ef5cf-134">Kayıt defteri anahtarı salt okunurdur ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="ef5cf-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="ef5cf-135">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ef5cf-135">.NET Framework Security</span></span>

<span data-ttu-id="ef5cf-136">Bu işlemi çalıştırmak için, derlemeniz sınıf tarafından verilen bir ayrıcalık düzeyi gerektiriyor <xref:System.Security.Permissions.RegistryPermission> .</span><span class="sxs-lookup"><span data-stu-id="ef5cf-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="ef5cf-137">Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ef5cf-138">Benzer şekilde, Kullanıcı oluşturma veya ayarları yazma için doğru ACL 'Lere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="ef5cf-139">Örneğin, kod erişim güvenliği iznine sahip bir yerel uygulama işletim sistemi iznine sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="ef5cf-140">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ef5cf-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef5cf-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef5cf-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="ef5cf-142">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="ef5cf-142">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="ef5cf-143">Kod Erişim Güvenliği Temelleri</span><span class="sxs-lookup"><span data-stu-id="ef5cf-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
