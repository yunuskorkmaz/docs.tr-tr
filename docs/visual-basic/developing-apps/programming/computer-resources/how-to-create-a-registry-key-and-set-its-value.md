---
title: 'Nasıl Yapılır: Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama'
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
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349195"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="e1f8e-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e1f8e-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="e1f8e-103">`My.Computer.Registry` Nesnenin `CreateSubKey` yöntemi bir kayıt defteri anahtarı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="e1f8e-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="e1f8e-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="e1f8e-105">Kayıt defteri anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e1f8e-105">To create a registry key</span></span>

- <span data-ttu-id="e1f8e-106">Anahtarın `CreateSubKey` altına hangi kovan yerleştirirken anahtarın adını belirterek yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="e1f8e-107">Parametre `Subkey` büyük/küçük harf duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="e1f8e-108">Bu örnek, HKEY_CURRENT_USER altında `MyTestKey` kayıt defteri anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="e1f8e-109">Kayıt defteri anahtarı oluşturmak ve içinde bir değer ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e1f8e-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="e1f8e-110">Anahtarın `CreateSubkey` altına hangi kovan yerleştirirken anahtarın adını belirterek yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="e1f8e-111">Bu örnek, HKEY_CURRENT_USER altında `MyTestKey` kayıt defteri anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="e1f8e-112">`SetValue` Yöntemi ile değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="e1f8e-113">Bu örnek, dize değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-113">This example sets the string value.</span></span> <span data-ttu-id="e1f8e-114">"MyTestKeyValue" için "Bu bir test değeri".</span><span class="sxs-lookup"><span data-stu-id="e1f8e-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="e1f8e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1f8e-115">Example</span></span>

<span data-ttu-id="e1f8e-116">Bu örnek, HKEY_CURRENT_USER altında `MyTestKey` kayıt defteri anahtarı nı `MyTestKeyValue` `This is a test value`oluşturur ve dize değerini .</span><span class="sxs-lookup"><span data-stu-id="e1f8e-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="e1f8e-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e1f8e-117">Robust Programming</span></span>

<span data-ttu-id="e1f8e-118">Anahtarınız için uygun bir yer bulmak için kayıt defteri yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="e1f8e-119">Örneğin, geçerli kullanıcının HKEY_CURRENT_USER\Yazılım anahtarını açmak ve şirketinizin adını içeren bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="e1f8e-120">Ardından şirket defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="e1f8e-121">Bir Web uygulamasından kayıt defterini okurken, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="e1f8e-122">Yerel bilgisayara () değil, kullanıcı<xref:Microsoft.Win32.Registry.CurrentUser>klasörüne veri yazmak<xref:Microsoft.Win32.Registry.LocalMachine>daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="e1f8e-123">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapacağınız gerektiğine karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="e1f8e-124">Başka bir işlem, belki de kötü niyetli bir, zaten değer yarattı ve ona erişimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="e1f8e-125">Verileri kayıt defteri değerine koyduğunuzda, veriler diğer işlem için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="e1f8e-126">Bunu önlemek için <xref:Microsoft.Win32.RegistryKey.GetValue%2A> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="e1f8e-127">Anahtar `Nothing` zaten yoksa döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="e1f8e-128">Kayıt defteri anahtarı ALA'lar (Access Control Lists) tarafından korunsa bile, parolalar gibi sırları kayıt defterinde düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="e1f8e-129">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="e1f8e-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="e1f8e-130">Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="e1f8e-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="e1f8e-131">Kullanıcının kayıt defteri anahtarları oluşturma izinleri<xref:System.Security.SecurityException>yoktur ( ).</span><span class="sxs-lookup"><span data-stu-id="e1f8e-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="e1f8e-132">Anahtar adı 255 karakter sınırını aşıyor<xref:System.ArgumentException>( ).</span><span class="sxs-lookup"><span data-stu-id="e1f8e-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="e1f8e-133">Anahtar kapalıdır<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="e1f8e-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="e1f8e-134">Kayıt defteri anahtarı salt okunur<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="e1f8e-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="e1f8e-135">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e1f8e-135">.NET Framework Security</span></span>

<span data-ttu-id="e1f8e-136">Bu işlemi çalıştırmak için derlemeniz <xref:System.Security.Permissions.RegistryPermission> sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="e1f8e-137">Kısmi güven bağlamında çalışıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="e1f8e-138">Benzer şekilde, kullanıcının ayarlar oluşturmak veya yazmak için doğru ALA'lara sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="e1f8e-139">Örneğin, kod erişim güvenlik iznine sahip yerel bir uygulamanın işletim sistemi izni olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="e1f8e-140">Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1f8e-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1f8e-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="e1f8e-142">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="e1f8e-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="e1f8e-143">Kod Erişim Güvenliği Temelleri</span><span class="sxs-lookup"><span data-stu-id="e1f8e-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
