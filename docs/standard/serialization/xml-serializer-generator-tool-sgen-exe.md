---
title: XML seri hale getirici Oluşturma Aracı (Sgen.exe)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 90b9a4fdbf5c341d128f768ed6825d1e2e465a82
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="9a690-102">XML seri hale getirici Oluşturma Aracı (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="9a690-102">XML Serializer Generator Tool (Sgen.exe)</span></span>
<span data-ttu-id="9a690-103">XML seri hale getirici oluşturucunun bir XML serileştirme derleme türleri için başlangıç performansını artırmak için belirtilen derlemesinde oluşturur bir <xref:System.Xml.Serialization.XmlSerializer> zaman serileştiren veya belirtilen türden nesneler seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9a690-103">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly in order to improve the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a690-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a690-104">Syntax</span></span>  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a690-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a690-105">Parameters</span></span>  
  
|<span data-ttu-id="9a690-106">Seçenek</span><span class="sxs-lookup"><span data-stu-id="9a690-106">Option</span></span>|<span data-ttu-id="9a690-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a690-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9a690-108">**/a**[**ssembly**] **: *** filename*</span><span class="sxs-lookup"><span data-stu-id="9a690-108">**/a**[**ssembly**]**:***filename*</span></span>|<span data-ttu-id="9a690-109">Tüm derlemesinde bulunan türleri veya tarafından belirtilen yürütülebilir dosya için seri hale getirme kod oluşturur *filename*.</span><span class="sxs-lookup"><span data-stu-id="9a690-109">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="9a690-110">Yalnızca bir dosya adı sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9a690-110">Only one file name can be provided.</span></span> <span data-ttu-id="9a690-111">Bu bağımsız değişken yinelenir, son dosya adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a690-111">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="9a690-112">**/c [ompiler]:** *seçenekleri*</span><span class="sxs-lookup"><span data-stu-id="9a690-112">**/c[ompiler]:** *options*</span></span>|<span data-ttu-id="9a690-113">C# Derleyici geçirilecek seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a690-113">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="9a690-114">Tüm csc.exe seçenekleri için derleyici geçirilen desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9a690-114">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="9a690-115">Bu derleme imzalanması gerektiğini belirtmek ve anahtar dosyasını belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a690-115">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="9a690-116">**/d**[**ebug**]</span><span class="sxs-lookup"><span data-stu-id="9a690-116">**/d**[**ebug**]</span></span>|<span data-ttu-id="9a690-117">Bir hata ayıklayıcısı ile kullanılan bir görüntü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a690-117">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="9a690-118">**/f [orce]**</span><span class="sxs-lookup"><span data-stu-id="9a690-118">**/f[orce]**</span></span>|<span data-ttu-id="9a690-119">Aynı ada sahip bir varolan derlemenin üzerine zorlar.</span><span class="sxs-lookup"><span data-stu-id="9a690-119">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="9a690-120">Varsayılan değer **false**.</span><span class="sxs-lookup"><span data-stu-id="9a690-120">The default is **false**.</span></span>|  
|<span data-ttu-id="9a690-121">**/ help veya /?**</span><span class="sxs-lookup"><span data-stu-id="9a690-121">**/help or /?**</span></span>|<span data-ttu-id="9a690-122">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9a690-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="9a690-123">**/ k**[**almayı durumunu Sürdür**]</span><span class="sxs-lookup"><span data-stu-id="9a690-123">**/k**[**eep**]</span></span>|<span data-ttu-id="9a690-124">Serileştirme derlemeye derlenen sonra oluşturulan kaynak dosyaların ve diğer geçici dosyaları silmeyi göstermez.</span><span class="sxs-lookup"><span data-stu-id="9a690-124">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="9a690-125">Bu araç belirli bir tür için serileştirme kod oluşturmak olup olmadığını belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a690-125">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="9a690-126">**/n**[**ologo**]</span><span class="sxs-lookup"><span data-stu-id="9a690-126">**/n**[**ologo**]</span></span>|<span data-ttu-id="9a690-127">Microsoft başlangıç başlığı görüntülenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="9a690-127">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="9a690-128">**/o**[**ut**] **: *** yolu*</span><span class="sxs-lookup"><span data-stu-id="9a690-128">**/o**[**ut**]**:***path*</span></span>|<span data-ttu-id="9a690-129">Oluşturulan derleme kaydedileceği dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a690-129">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="9a690-130">**Not:** oluşturulan derleme adını giriş derleme artı "xmlSerializers.dll" adından oluşur.</span><span class="sxs-lookup"><span data-stu-id="9a690-130">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="9a690-131">**/p**[**roxytypes**]</span><span class="sxs-lookup"><span data-stu-id="9a690-131">**/p**[**roxytypes**]</span></span>|<span data-ttu-id="9a690-132">XML Web hizmeti proxy türleri için yalnızca serileştirme kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a690-132">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="9a690-133">**/r**[**vuru**] **: *** assemblyfiles*</span><span class="sxs-lookup"><span data-stu-id="9a690-133">**/r**[**eference**]**:***assemblyfiles*</span></span>|<span data-ttu-id="9a690-134">XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a690-134">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="9a690-135">Virgülle ayrılmış birden çok derleme dosyaları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a690-135">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="9a690-136">**/s**[**ilent**]</span><span class="sxs-lookup"><span data-stu-id="9a690-136">**/s**[**ilent**]</span></span>|<span data-ttu-id="9a690-137">Başarı iletilerinin görüntülenmesini bastırır.</span><span class="sxs-lookup"><span data-stu-id="9a690-137">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="9a690-138">**/t**[**türü**] **: *** türü*</span><span class="sxs-lookup"><span data-stu-id="9a690-138">**/t**[**ype**]**:***type*</span></span>|<span data-ttu-id="9a690-139">Belirtilen tür için yalnızca serileştirme kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a690-139">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="9a690-140">**/v**[**erbose**]</span><span class="sxs-lookup"><span data-stu-id="9a690-140">**/v**[**erbose**]</span></span>|<span data-ttu-id="9a690-141">Hata ayıklama için ayrıntılı çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9a690-141">Displays verbose output for debugging.</span></span> <span data-ttu-id="9a690-142">Listeler ile seri hale getirilemiyor hedef derleme türlerinden <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9a690-142">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="9a690-143">**/?**</span><span class="sxs-lookup"><span data-stu-id="9a690-143">**/?**</span></span>|<span data-ttu-id="9a690-144">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9a690-144">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a690-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a690-145">Remarks</span></span>  
 <span data-ttu-id="9a690-146">XML seri hale getirici oluşturucunun kullanılmadığında bir <xref:System.Xml.Serialization.XmlSerializer> seri hale getirme kodu ve bir seri hale getirme derlemesi her türü için bir uygulama her çalıştırıldığında oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a690-146">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="9a690-147">XML serileştirme başlangıç performansını artırmak için bu derlemeler önceden oluşturmak üzere Sgen.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a690-147">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="9a690-148">Bu derlemeleri uygulama ile sonra dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a690-148">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="9a690-149">XML seri hale getirici oluşturucunun ayrıca seri hale getirme işlemi türü ilk kez yüklendiğinde isabet bir performans tabi olmayan çünkü sunucularla iletişim kurmak için XML Web hizmeti proxy kullanan istemciler performansını geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9a690-149">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="9a690-150">Bu oluşturulan derlemeler bir Web hizmeti sunucu tarafında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9a690-150">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="9a690-151">Bu, yalnızca Web hizmeti istemcileri ve el ile serileştirme senaryolar için aracıdır.</span><span class="sxs-lookup"><span data-stu-id="9a690-151">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="9a690-152">Serileştirilecek tür içeren derlemenin MyType.dll adlandırılmışsa, ardından ilişkili seri hale getirme derlemesi MyType.XmlSerializers.dll olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9a690-152">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9a690-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9a690-153">Examples</span></span>  
 <span data-ttu-id="9a690-154">Aşağıdaki komutu Data.dll adlı derlemesinde bulunan tüm türleri serileştirmek için Data.XmlSerializers.dll adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a690-154">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```  
sgen Data.dll   
```  
  
 <span data-ttu-id="9a690-155">Seri hale getirmek ve Data.dll türlerinde seri durumdan çıkarılacağı kodundan Data.XmlSerializers.dll derleme başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="9a690-155">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a690-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a690-156">See Also</span></span>  
 [<span data-ttu-id="9a690-157">Araçlar</span><span class="sxs-lookup"><span data-stu-id="9a690-157">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="9a690-158">XML Web Hizmetleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="9a690-158">XML Web Services Overview</span></span>](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [<span data-ttu-id="9a690-159">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="9a690-159">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
