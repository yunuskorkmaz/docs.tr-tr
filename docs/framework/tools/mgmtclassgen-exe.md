---
title: "Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f3e01e54cb60c7da1a57940246c5402ba635778
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="62903-102">Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="62903-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="62903-103">Yönetim Kesin Belirlenmiş Sınıf Üreticisi aracı, belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için erken bağlı yönetilen bir sınıfı hızlı bir şekilde üretmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="62903-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="62903-104">Oluşturulan sınıf, WMI sınıfının bir örneğine erişmek için yazmanız gereken kodu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="62903-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62903-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62903-105">Syntax</span></span>  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|<span data-ttu-id="62903-106">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="62903-106">Argument</span></span>|<span data-ttu-id="62903-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62903-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="62903-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="62903-108">*WMIClass*</span></span>|<span data-ttu-id="62903-109">Kendisi için erken bağlı yönetilen bir sınıf oluşturulacak Windows Yönetim Araçları sınıfı.</span><span class="sxs-lookup"><span data-stu-id="62903-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="62903-110">Seçenek</span><span class="sxs-lookup"><span data-stu-id="62903-110">Option</span></span>|<span data-ttu-id="62903-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62903-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="62903-112">**/l***dili* </span><span class="sxs-lookup"><span data-stu-id="62903-112">**/l**  *language*</span></span>|<span data-ttu-id="62903-113">Erken bağlı yönetilen sınıfın oluşturulacağı dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="62903-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="62903-114">Belirleyebileceğiniz **CS** (C#; varsayılan), **VB** (Visual Basic) **MC** (C++) veya **JS** (JScript) dil bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="62903-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="62903-115">**/m***makine* </span><span class="sxs-lookup"><span data-stu-id="62903-115">**/m**  *machine*</span></span>|<span data-ttu-id="62903-116">WMI sınıfının bulunduğu, bağlanılacak bilgisayarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="62903-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="62903-117">Varsayılan, yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="62903-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="62903-118">**/n**  *yol*</span><span class="sxs-lookup"><span data-stu-id="62903-118">**/n**  *path*</span></span>|<span data-ttu-id="62903-119">WMI sınıfını içeren WMI ad alanına giden yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="62903-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="62903-120">Bu seçeneği belirtmezseniz, araç için kod oluşturur *WMIClass* varsayılan **Root\cimv2** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="62903-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="62903-121">**/o***classnamespace* </span><span class="sxs-lookup"><span data-stu-id="62903-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="62903-122">Yönetilen kod sınıfının içinde üretileceği .NET ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62903-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="62903-123">Bu seçeneği belirtmezseniz, araç ad alanını WMI ad alanını ve şema önekini kullanarak üretir.</span><span class="sxs-lookup"><span data-stu-id="62903-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="62903-124">Şema öneki, sınıf adının alt çizgi karakterinden önce gelen parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="62903-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="62903-125">Örneğin, **Win32_OperatingSystem** sınıfını **Root\cimv2** ad alanı, oluşturma aracı sınıfında **kök. CIMV2. Win32**.</span><span class="sxs-lookup"><span data-stu-id="62903-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="62903-126">**/p***filepath* </span><span class="sxs-lookup"><span data-stu-id="62903-126">**/p**  *filepath*</span></span>|<span data-ttu-id="62903-127">Üretilen kodun içinde kaydedileceği dosyanın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="62903-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="62903-128">Bu seçeneği belirtmezseniz, araç dosyayı geçerli dizinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62903-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="62903-129">Oluşturur sınıfını kullanarak dosya ve sınıf adları *WMIClass* bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="62903-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="62903-130">Sınıf ve dosya adını adı aynı olan *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="62903-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="62903-131">Varsa *WMIClass* bir alt çizgi karakteri içeren alt çizgi karakterini izleyen sınıf adı bölümü Aracı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="62903-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="62903-132">Örneğin, varsa *WMIClass* adıdır biçiminde **Win32_LogicalDisk**, oluşturulan sınıf ve dosya "MantıksalDisk" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="62903-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="62903-133">Bir dosya zaten varsa, araç varolan dosyanın üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="62903-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="62903-134">**/pw***parola* </span><span class="sxs-lookup"><span data-stu-id="62903-134">**/pw**  *password*</span></span>|<span data-ttu-id="62903-135">Tarafından belirtilen bir bilgisayara oturum açarken kullanılacak parolayı belirtir **/m** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="62903-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="62903-136">**/u***kullanıcı adı* </span><span class="sxs-lookup"><span data-stu-id="62903-136">**/u**  *user name*</span></span>|<span data-ttu-id="62903-137">Tarafından belirtilen bir bilgisayara oturum açarken kullanılacak kullanıcı adını belirtir **/m** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="62903-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="62903-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="62903-138">**/?**</span></span>|<span data-ttu-id="62903-139">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="62903-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62903-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62903-140">Remarks</span></span>  
 <span data-ttu-id="62903-141">MgmtClassGen.exe kullanan <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="62903-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="62903-142">Bu nedenle, C#, Visual Basic ve JScript'ten başka yönetilen dillerde kod üretmek için, herhangi bir özel kod sağlayıcısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62903-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="62903-143">Üretilen sınıfların, kendisi için üretildikleri şemaya bağlı olduklarını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="62903-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="62903-144">Arka plandaki şema değişirse, şemada yapılan değişiklikleri yansıtmasını isterseniz, sınıfı yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62903-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="62903-145">Aşağıdaki tabloda, WMI Ortak Bilgi Modeli (CIM) türlerinin üretilmiş bir sınıftaki veri türleriyle nasıl eşleştiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="62903-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="62903-146">CIM türü</span><span class="sxs-lookup"><span data-stu-id="62903-146">CIM type</span></span>|<span data-ttu-id="62903-147">Oluşturulan sınıf içinde veri türü</span><span class="sxs-lookup"><span data-stu-id="62903-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="62903-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="62903-148">CIM_SINT8</span></span>|<span data-ttu-id="62903-149">**SByte**</span><span class="sxs-lookup"><span data-stu-id="62903-149">**SByte**</span></span>|  
|<span data-ttu-id="62903-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="62903-150">CIM_UINT8</span></span>|<span data-ttu-id="62903-151">**Bayt**</span><span class="sxs-lookup"><span data-stu-id="62903-151">**Byte**</span></span>|  
|<span data-ttu-id="62903-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="62903-152">CIM_SINT16</span></span>|<span data-ttu-id="62903-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="62903-153">**Int16**</span></span>|  
|<span data-ttu-id="62903-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="62903-154">CIM_UINT16</span></span>|<span data-ttu-id="62903-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="62903-155">**UInt16**</span></span>|  
|<span data-ttu-id="62903-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="62903-156">CIM_SINT32</span></span>|<span data-ttu-id="62903-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="62903-157">**Int32**</span></span>|  
|<span data-ttu-id="62903-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="62903-158">SIM_UINT32</span></span>|<span data-ttu-id="62903-159">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="62903-159">**UInt32**</span></span>|  
|<span data-ttu-id="62903-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="62903-160">CIM_SINT64</span></span>|<span data-ttu-id="62903-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="62903-161">**Int64**</span></span>|  
|<span data-ttu-id="62903-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="62903-162">CIM_UINT64</span></span>|<span data-ttu-id="62903-163">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="62903-163">**UInt64**</span></span>|  
|<span data-ttu-id="62903-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="62903-164">CIM_REAL32</span></span>|<span data-ttu-id="62903-165">**Tek**</span><span class="sxs-lookup"><span data-stu-id="62903-165">**Single**</span></span>|  
|<span data-ttu-id="62903-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="62903-166">CIM_REAL64</span></span>|<span data-ttu-id="62903-167">**Çift**</span><span class="sxs-lookup"><span data-stu-id="62903-167">**Double**</span></span>|  
|<span data-ttu-id="62903-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="62903-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="62903-169">**Boole değeri**</span><span class="sxs-lookup"><span data-stu-id="62903-169">**Boolean**</span></span>|  
|<span data-ttu-id="62903-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="62903-170">CIM_String</span></span>|<span data-ttu-id="62903-171">**Dize**</span><span class="sxs-lookup"><span data-stu-id="62903-171">**String**</span></span>|  
|<span data-ttu-id="62903-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="62903-172">CIM_DATETIME</span></span>|<span data-ttu-id="62903-173">**DateTime** veya **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="62903-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="62903-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="62903-174">CIM_REFERENCE</span></span>|<span data-ttu-id="62903-175">**ManagementPath'i**</span><span class="sxs-lookup"><span data-stu-id="62903-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="62903-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="62903-176">CIM_CHAR16</span></span>|<span data-ttu-id="62903-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="62903-177">**Char**</span></span>|  
|<span data-ttu-id="62903-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="62903-178">CIM_OBJECT</span></span>|<span data-ttu-id="62903-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="62903-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="62903-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="62903-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="62903-181">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="62903-181">**Object**</span></span>|  
|<span data-ttu-id="62903-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="62903-182">CIM_ARRAY</span></span>|<span data-ttu-id="62903-183">Yukarıda sözü edilen nesnelerin dizisi</span><span class="sxs-lookup"><span data-stu-id="62903-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="62903-184">Bir WMI sınıfı oluşturduğunuzda, aşağıdaki davranışlara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="62903-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
-   <span data-ttu-id="62903-185">Standart bir genel özelliğin veya yöntemin, varolan bir özellikle veya yöntemle aynı ada sahip olması olanaklıdır.</span><span class="sxs-lookup"><span data-stu-id="62903-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="62903-186">Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="62903-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="62903-187">Oluşturulan bir sınıftaki bir özellik veya yöntemin adının hedef programlama dilinde bir anahtar sözcük olması olanaklıdır.</span><span class="sxs-lookup"><span data-stu-id="62903-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="62903-188">Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="62903-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="62903-189">WMI'da, niteleyiciler bir sınıfı, örneği, özelliği veya yöntemi tanımlamak için bilgi içeren değiştiricilerdir.</span><span class="sxs-lookup"><span data-stu-id="62903-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="62903-190">WMI kullanan standart niteleyicileri gibi **okuma**, **yazma**, ve **anahtar** oluşturulan sınıf özelliğinde açıklamak için.</span><span class="sxs-lookup"><span data-stu-id="62903-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="62903-191">Örneğin, ile değiştiren bir özelliği bir **okuma** niteleyicisi yalnızca özelliğiyle tanımlanmış **almak** oluşturulan sınıf erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="62903-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="62903-192">Bir özellik ile işaretlediğinden **okuma** niteleyicisi salt okunur olacak şekilde tasarlanmıştır bir **ayarlamak** erişimci tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="62903-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
-   <span data-ttu-id="62903-193">Sayısal bir özellik tarafından değiştirilebilir **değerleri** ve **ValueMaps** niteleyicileri özelliği yalnızca ayarlanabilir belirtmek için izin verilebilir değerler belirtildi.</span><span class="sxs-lookup"><span data-stu-id="62903-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="62903-194">Numaralandırma bunlarla oluşturulan **değerleri** ve **ValueMaps** ve özellik numaralandırma eşlendi.</span><span class="sxs-lookup"><span data-stu-id="62903-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
-   <span data-ttu-id="62903-195">WMI, yalnızca bir örneği olabilecek bir sınıf tanımlamak için singleton terimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="62903-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="62903-196">Bu nedenle, tek bir singleton sınıfı için varsayılan oluşturucu, sınıfı sınıfın tek örneğine hazırlar.</span><span class="sxs-lookup"><span data-stu-id="62903-196">Therefore, the default constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
-   <span data-ttu-id="62903-197">Bir WMI sınıfının, nesne olan özellikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="62903-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="62903-198">Bu tür WMI sınıfı için kesin olarak belirlenmiş bir sınıf ürettiğinizde, gömülü nesne özellikleri türleri için kesin olarak belirlenmiş türler oluşturmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="62903-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="62903-199">Bu, gömülü nesnelere kesin olarak belirlenmiş bir şekilde erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="62903-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="62903-200">Üretilen kodun gömülü nesnenin türünü algılayamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="62903-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="62903-201">Bu durumda, sorunu size bildirmek için, üretilen kodda bir açıklama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62903-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="62903-202">Sonra, özelliği üretilen diğer sınıfa yazmak için, üretilen kodu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62903-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
-   <span data-ttu-id="62903-203">WMI'da, CIM_DATETIME veri türünün veri değeri belirli bir tarih ve saati veya bir zaman aralığını gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="62903-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="62903-204">Bir tarih ve saat veri değerini temsil eder, oluşturulan sınıfın veri türü ise **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="62903-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="62903-205">Veri değeri bir zaman aralığı temsil ediyorsa, oluşturulan sınıfın veri türü olan **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="62903-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="62903-206">Alternatif olarak, Visual Studio .NET'te Sunucu Gezgini Yönetim Uzantısı'nı kullanarak, kesin olarak belirlenmiş bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62903-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="62903-207">WMI hakkında daha fazla bilgi için bkz: **Windows Yönetim Araçları** konuda Platform SDK Belgeleri.</span><span class="sxs-lookup"><span data-stu-id="62903-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="62903-208">Örnekler</span><span class="sxs-lookup"><span data-stu-id="62903-208">Examples</span></span>  
 <span data-ttu-id="62903-209">Aşağıdaki komutu bir yönetilen Sınıf C# kodunu oluşturur **Win32_LogicalDisk** WMI sınıfında **Root\cimv2** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="62903-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="62903-210">Aracı yönetilen sınıf içinde c:\disk.cs konumundaki kaynak dosyasına yazar **kök. CIMV2. Win32** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="62903-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="62903-211">Aşağıdaki kod örneği, oluşturulan bir sınıfın programsal olarak nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="62903-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="62903-212">İlk olarak, sınıfın bir örneği numaralandırılır ve yol yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="62903-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="62903-213">Ardından, başlatılacak oluşturulan sınıfın bir örneği bir WMI örneğiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62903-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="62903-214">`Process`oluşturulan sınıf **Win32_Process** ve `LogicalDisk` için oluşturulan sınıf **Win32_LogicalDisk** içinde **Root\cimv2** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="62903-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="62903-215">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62903-215">See Also</span></span>  
 <xref:System.Management>  
 <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>  
 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>  
 [<span data-ttu-id="62903-216">Araçları</span><span class="sxs-lookup"><span data-stu-id="62903-216">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="62903-217">Komut istemleri</span><span class="sxs-lookup"><span data-stu-id="62903-217">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
