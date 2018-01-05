---
title: Derlemeleri COM ile Kaydetme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1473fa07b57dcd19ea192db6cdb0a395f119b159
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="fbf9d-102">Derlemeleri COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="fbf9d-102">Registering Assemblies with COM</span></span>
<span data-ttu-id="fbf9d-103">Adlı bir komut satırı aracını çalıştırabilirsiniz [derleme Kayıt Aracı (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) kaydetmek veya com ile kullanmak için bir derleme kaydını kaldırma</span><span class="sxs-lookup"><span data-stu-id="fbf9d-103">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="fbf9d-104">COM istemcileri .NET Framework sınıf şeffaf bir şekilde kullanabilmeniz için Regasm.exe Sistem kayıt defterine sınıfı hakkında bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-104">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="fbf9d-105"><xref:System.Runtime.InteropServices.RegistrationServices> Sınıfı eşdeğer işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-105">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="fbf9d-106">Bir COM istemciden etkinleştirilmeden önce yönetilen bileşenin Windows Kayıt Defteri'nde kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-106">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="fbf9d-107">Aşağıdaki tabloda Regasm.exe genellikle Windows kayıt defterine ekler anahtarlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-107">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="fbf9d-108">(000000 gerçek GUID değeri gösterir.)</span><span class="sxs-lookup"><span data-stu-id="fbf9d-108">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="fbf9d-109">GUID</span><span class="sxs-lookup"><span data-stu-id="fbf9d-109">GUID</span></span>|<span data-ttu-id="fbf9d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbf9d-110">Description</span></span>|<span data-ttu-id="fbf9d-111">Kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="fbf9d-111">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="fbf9d-112">CLSID</span><span class="sxs-lookup"><span data-stu-id="fbf9d-112">CLSID</span></span>|<span data-ttu-id="fbf9d-113">Sınıf tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="fbf9d-113">Class identifier</span></span>|<span data-ttu-id="fbf9d-114">HKEY_CLASSES_ROOT\CLSID\\{000... 000}</span><span class="sxs-lookup"><span data-stu-id="fbf9d-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="fbf9d-115">IID</span><span class="sxs-lookup"><span data-stu-id="fbf9d-115">IID</span></span>|<span data-ttu-id="fbf9d-116">Arabirim tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="fbf9d-116">Interface identifier</span></span>|<span data-ttu-id="fbf9d-117">HKEY_CLASSES_ROOT\Interface\\{000... 000}</span><span class="sxs-lookup"><span data-stu-id="fbf9d-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="fbf9d-118">KİTAPLIK KİMLİĞİ</span><span class="sxs-lookup"><span data-stu-id="fbf9d-118">LIBID</span></span>|<span data-ttu-id="fbf9d-119">Tür kitaplığı tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="fbf9d-119">Library identifier</span></span>|<span data-ttu-id="fbf9d-120">HKEY_CLASSES_ROOT\TypeLib\\{000... 000}</span><span class="sxs-lookup"><span data-stu-id="fbf9d-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="fbf9d-121">ProgID</span><span class="sxs-lookup"><span data-stu-id="fbf9d-121">ProgID</span></span>|<span data-ttu-id="fbf9d-122">Program tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="fbf9d-122">Programmatic identifier</span></span>|<span data-ttu-id="fbf9d-123">HKEY_CLASSES_ROOT\000... 000</span><span class="sxs-lookup"><span data-stu-id="fbf9d-123">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="fbf9d-124">HKCR\CLSID altında\\{0000... 0000} anahtarı, varsayılan değer sınıfı ProgID için ayarlanır ve iki yeni adlandırılmış değerler, sınıf ve derlemeyi eklenir.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-124">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="fbf9d-125">Çalışma zamanı derlemesi değerini kayıt defterinden okur ve çalışma zamanı derlemesi çözümleyicisini açın geçirir.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-125">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="fbf9d-126">Derleme Çözümleyicisi ad ve sürüm numarası gibi derleme bilgilere dayalı derleme bulmayı dener.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-126">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="fbf9d-127">Derleme Çözümleyicisi bütünleştirilmiş bulmak derleme aşağıdaki konumlardan birinde olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="fbf9d-127">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
-   <span data-ttu-id="fbf9d-128">Genel Derleme Önbelleği (tanımlayıcı adlı bir derleme olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="fbf9d-128">The global assembly cache (must be a strong-named assembly).</span></span>  
  
-   <span data-ttu-id="fbf9d-129">Uygulama dizini.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-129">In the application directory.</span></span> <span data-ttu-id="fbf9d-130">Uygulama yolu yüklenen derlemeler yalnızca bu uygulamadan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-130">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
-   <span data-ttu-id="fbf9d-131">İle belirtilen bir dosya yolu boyunca **/ codebase** Regasm.exe seçeneği.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-131">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="fbf9d-132">RegAsm.exe da HKCR\CLSID Inprocserver32 anahtarında oluşturur\\{0000... 0000} anahtarı.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-132">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="fbf9d-133">Anahtar için varsayılan değeri, ortak dil çalışma zamanı (Mscoree.dll) başlatır DLL adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-133">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="fbf9d-134">Kayıt Defteri Girdilerini İnceleme</span><span class="sxs-lookup"><span data-stu-id="fbf9d-134">Examining Registry Entries</span></span>  
 <span data-ttu-id="fbf9d-135">COM birlikte çalışma herhangi bir .NET Framework sınıf örneği oluşturmak için bir standart sınıf Fabrika uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-135">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="fbf9d-136">İstemcileri çağırabilir **DllGetClassObject** bir üreteci almak ve herhangi bir COM bileşeni ile gibi nesneleri oluşturmak için yönetilen DLL üzerinde.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-136">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="fbf9d-137">İçin `InprocServer32` alt anahtarı Mscoree.dll başvuru ortak dil çalışma zamanı yönetilen nesnesi oluşturur belirtmek için geleneksel COM tür kitaplığı yerine görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-137">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf9d-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbf9d-138">See Also</span></span>  
 [<span data-ttu-id="fbf9d-139">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="fbf9d-139">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="fbf9d-140">Nasıl yapılır: COM'dan .NET Türlerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="fbf9d-140">How to: Reference .NET Types from COM</span></span>](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
 [<span data-ttu-id="fbf9d-141">Bir .NET nesnesini çağırma</span><span class="sxs-lookup"><span data-stu-id="fbf9d-141">Calling a .NET Object</span></span>](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="fbf9d-142">COM erişim için bir uygulama dağıtma</span><span class="sxs-lookup"><span data-stu-id="fbf9d-142">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)
