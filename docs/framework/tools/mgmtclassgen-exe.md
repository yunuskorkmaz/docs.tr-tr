---
title: Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)
description: Yönetim türü kesin belirlenmiş sınıf oluşturucusunun Mgmtclassgen.exe anlayın. Bu araç, bir WMI sınıfı için hızlı bir şekilde önceden bağlantılı yönetilen sınıf oluşturmanıza olanak sağlar.
ms.date: 03/30/2017
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
ms.openlocfilehash: 89facd4369dad6168e46febd3e34d7f7c235faf0
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517301"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="b8267-104">Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="b8267-104">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="b8267-105">Yönetim Kesin Belirlenmiş Sınıf Üreticisi aracı, belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için erken bağlı yönetilen bir sınıfı hızlı bir şekilde üretmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b8267-105">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="b8267-106">Oluşturulan sınıf, WMI sınıfının bir örneğine erişmek için yazmanız gereken kodu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b8267-106">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8267-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b8267-107">Syntax</span></span>  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|<span data-ttu-id="b8267-108">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="b8267-108">Argument</span></span>|<span data-ttu-id="b8267-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8267-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b8267-110">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="b8267-110">*WMIClass*</span></span>|<span data-ttu-id="b8267-111">Kendisi için erken bağlı yönetilen bir sınıf oluşturulacak Windows Yönetim Araçları sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8267-111">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="b8267-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="b8267-112">Option</span></span>|<span data-ttu-id="b8267-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8267-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b8267-114">**/l**  *dili*</span><span class="sxs-lookup"><span data-stu-id="b8267-114">**/l**  *language*</span></span>|<span data-ttu-id="b8267-115">Erken bağlı yönetilen sınıfın oluşturulacağı dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8267-115">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="b8267-116">**CS** (C#; varsayılan), **vb** (Visual Basic), **mc** (C++) veya **js** (JScript) dilini bağımsız değişkeni olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8267-116">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="b8267-117">**/m**  *makinesi*</span><span class="sxs-lookup"><span data-stu-id="b8267-117">**/m**  *machine*</span></span>|<span data-ttu-id="b8267-118">WMI sınıfının bulunduğu, bağlanılacak bilgisayarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8267-118">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="b8267-119">Varsayılan, yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="b8267-119">The default is the local computer.</span></span>|  
|<span data-ttu-id="b8267-120">**/n**  *yolu*</span><span class="sxs-lookup"><span data-stu-id="b8267-120">**/n**  *path*</span></span>|<span data-ttu-id="b8267-121">WMI sınıfını içeren WMI ad alanına giden yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8267-121">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="b8267-122">Bu seçeneği belirtmezseniz, araç varsayılan **root\cimv2** ad alanında *WMIClass* için kod üretir.</span><span class="sxs-lookup"><span data-stu-id="b8267-122">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="b8267-123">**/o**  *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="b8267-123">**/o**  *classnamespace*</span></span>|<span data-ttu-id="b8267-124">Yönetilen kod sınıfının içinde üretileceği .NET ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8267-124">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="b8267-125">Bu seçeneği belirtmezseniz, araç ad alanını WMI ad alanını ve şema önekini kullanarak üretir.</span><span class="sxs-lookup"><span data-stu-id="b8267-125">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="b8267-126">Şema öneki, sınıf adının alt çizgi karakterinden önce gelen parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b8267-126">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="b8267-127">Örneğin, **root\cimv2** ad alanındaki **Win32_OperatingSystem** sınıfı Için, araç sınıfı kök içinde oluşturur **. CIMV2. Win32**.</span><span class="sxs-lookup"><span data-stu-id="b8267-127">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="b8267-128">**/p**  *FilePath*</span><span class="sxs-lookup"><span data-stu-id="b8267-128">**/p**  *filepath*</span></span>|<span data-ttu-id="b8267-129">Üretilen kodun içinde kaydedileceği dosyanın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8267-129">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="b8267-130">Bu seçeneği belirtmezseniz, araç dosyayı geçerli dizinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8267-130">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="b8267-131">*WMIClass* bağımsız değişkenini kullanarak sınıfının oluşturduğu sınıf ve dosyayı adlandırır.</span><span class="sxs-lookup"><span data-stu-id="b8267-131">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="b8267-132">Sınıfın adı ve dosya, WMIClass adıyla aynıdır *.*</span><span class="sxs-lookup"><span data-stu-id="b8267-132">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="b8267-133">*WMIClass* bir alt çizgi karakteri içeriyorsa, araç alt çizgi karakterini izleyen sınıf adının bölümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8267-133">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="b8267-134">Örneğin, *WMIClass* adı **Win32_LogicalDisk**biçimindeyse, oluşturulan sınıf ve dosya "MantıksalDisk" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8267-134">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="b8267-135">Bir dosya zaten varsa, araç varolan dosyanın üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="b8267-135">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="b8267-136">**/PW**  *parolası*</span><span class="sxs-lookup"><span data-stu-id="b8267-136">**/pw**  *password*</span></span>|<span data-ttu-id="b8267-137">**/M** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak parolayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8267-137">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="b8267-138">**/u**  *Kullanıcı adı*</span><span class="sxs-lookup"><span data-stu-id="b8267-138">**/u**  *user name*</span></span>|<span data-ttu-id="b8267-139">**/M** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak kullanıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8267-139">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="b8267-140">**/?**</span><span class="sxs-lookup"><span data-stu-id="b8267-140">**/?**</span></span>|<span data-ttu-id="b8267-141">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b8267-141">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8267-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8267-142">Remarks</span></span>  
 <span data-ttu-id="b8267-143">Mgmtclassgen.exe yöntemini kullanır <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b8267-143">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b8267-144">Bu nedenle, C#, Visual Basic ve JScript'ten başka yönetilen dillerde kod üretmek için, herhangi bir özel kod sağlayıcısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8267-144">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="b8267-145">Üretilen sınıfların, kendisi için üretildikleri şemaya bağlı olduklarını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b8267-145">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="b8267-146">Arka plandaki şema değişirse, şemada yapılan değişiklikleri yansıtmasını isterseniz, sınıfı yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8267-146">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="b8267-147">Aşağıdaki tabloda, WMI Ortak Bilgi Modeli (CIM) türlerinin üretilmiş bir sınıftaki veri türleriyle nasıl eşleştiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b8267-147">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="b8267-148">CIM türü</span><span class="sxs-lookup"><span data-stu-id="b8267-148">CIM type</span></span>|<span data-ttu-id="b8267-149">Oluşturulan sınıf içinde veri türü</span><span class="sxs-lookup"><span data-stu-id="b8267-149">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="b8267-150">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="b8267-150">CIM_SINT8</span></span>|<span data-ttu-id="b8267-151">**SByte**</span><span class="sxs-lookup"><span data-stu-id="b8267-151">**SByte**</span></span>|  
|<span data-ttu-id="b8267-152">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="b8267-152">CIM_UINT8</span></span>|<span data-ttu-id="b8267-153">**Bayt**</span><span class="sxs-lookup"><span data-stu-id="b8267-153">**Byte**</span></span>|  
|<span data-ttu-id="b8267-154">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="b8267-154">CIM_SINT16</span></span>|<span data-ttu-id="b8267-155">**Int16**</span><span class="sxs-lookup"><span data-stu-id="b8267-155">**Int16**</span></span>|  
|<span data-ttu-id="b8267-156">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="b8267-156">CIM_UINT16</span></span>|<span data-ttu-id="b8267-157">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="b8267-157">**UInt16**</span></span>|  
|<span data-ttu-id="b8267-158">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="b8267-158">CIM_SINT32</span></span>|<span data-ttu-id="b8267-159">**Int32**</span><span class="sxs-lookup"><span data-stu-id="b8267-159">**Int32**</span></span>|  
|<span data-ttu-id="b8267-160">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="b8267-160">SIM_UINT32</span></span>|<span data-ttu-id="b8267-161">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="b8267-161">**UInt32**</span></span>|  
|<span data-ttu-id="b8267-162">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="b8267-162">CIM_SINT64</span></span>|<span data-ttu-id="b8267-163">**Tutulamaz**</span><span class="sxs-lookup"><span data-stu-id="b8267-163">**Int64**</span></span>|  
|<span data-ttu-id="b8267-164">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="b8267-164">CIM_UINT64</span></span>|<span data-ttu-id="b8267-165">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="b8267-165">**UInt64**</span></span>|  
|<span data-ttu-id="b8267-166">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="b8267-166">CIM_REAL32</span></span>|<span data-ttu-id="b8267-167">**Tek**</span><span class="sxs-lookup"><span data-stu-id="b8267-167">**Single**</span></span>|  
|<span data-ttu-id="b8267-168">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="b8267-168">CIM_REAL64</span></span>|<span data-ttu-id="b8267-169">**Çift**</span><span class="sxs-lookup"><span data-stu-id="b8267-169">**Double**</span></span>|  
|<span data-ttu-id="b8267-170">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="b8267-170">CIM_BOOLEAN</span></span>|<span data-ttu-id="b8267-171">**Boole**</span><span class="sxs-lookup"><span data-stu-id="b8267-171">**Boolean**</span></span>|  
|<span data-ttu-id="b8267-172">CIM_String</span><span class="sxs-lookup"><span data-stu-id="b8267-172">CIM_String</span></span>|<span data-ttu-id="b8267-173">**Dize**</span><span class="sxs-lookup"><span data-stu-id="b8267-173">**String**</span></span>|  
|<span data-ttu-id="b8267-174">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="b8267-174">CIM_DATETIME</span></span>|<span data-ttu-id="b8267-175">**DateTime** veya **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="b8267-175">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="b8267-176">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="b8267-176">CIM_REFERENCE</span></span>|<span data-ttu-id="b8267-177">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="b8267-177">**ManagementPath**</span></span>|  
|<span data-ttu-id="b8267-178">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="b8267-178">CIM_CHAR16</span></span>|<span data-ttu-id="b8267-179">**Char**</span><span class="sxs-lookup"><span data-stu-id="b8267-179">**Char**</span></span>|  
|<span data-ttu-id="b8267-180">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="b8267-180">CIM_OBJECT</span></span>|<span data-ttu-id="b8267-181">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="b8267-181">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="b8267-182">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="b8267-182">CIM_IUNKNOWN</span></span>|<span data-ttu-id="b8267-183">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="b8267-183">**Object**</span></span>|  
|<span data-ttu-id="b8267-184">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="b8267-184">CIM_ARRAY</span></span>|<span data-ttu-id="b8267-185">Yukarıda sözü edilen nesnelerin dizisi</span><span class="sxs-lookup"><span data-stu-id="b8267-185">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="b8267-186">Bir WMI sınıfı oluşturduğunuzda, aşağıdaki davranışlara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="b8267-186">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="b8267-187">Standart bir genel özelliğin veya yöntemin, varolan bir özellikle veya yöntemle aynı ada sahip olması olanaklıdır.</span><span class="sxs-lookup"><span data-stu-id="b8267-187">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="b8267-188">Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b8267-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="b8267-189">Oluşturulan bir sınıftaki bir özellik veya yöntemin adının hedef programlama dilinde bir anahtar sözcük olması olanaklıdır.</span><span class="sxs-lookup"><span data-stu-id="b8267-189">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="b8267-190">Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b8267-190">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="b8267-191">WMI'da, niteleyiciler bir sınıfı, örneği, özelliği veya yöntemi tanımlamak için bilgi içeren değiştiricilerdir.</span><span class="sxs-lookup"><span data-stu-id="b8267-191">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="b8267-192">WMI, oluşturulmuş bir sınıftaki bir özelliği tanımlamakta kullanılacak **Read**, **Write**ve **Key** gibi standart niteleyicileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8267-192">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="b8267-193">Örneğin, bir **okuma** niteleyicisi ile değiştirilen bir özellik yalnızca oluşturulan sınıfta bir özellik **Get** erişimcisi ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b8267-193">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="b8267-194">**Okuma** niteleyicisi ile işaretlenen bir özelliğin Salt okunabilir olması amaçlandığından, bir **küme** erişimcisi tanımlı değildir.</span><span class="sxs-lookup"><span data-stu-id="b8267-194">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="b8267-195">Değerin yalnızca belirtilen izin verilen değerlere ayarlanabileceği göstermek için **Values** ve **ValueMaps** niteleyicilerine göre sayısal bir özellik değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b8267-195">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="b8267-196">Bu **değerler** ve **ValueMaps** ile bir numaralandırma oluşturulur ve özellik sabit listesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="b8267-196">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="b8267-197">WMI, yalnızca bir örneği olabilecek bir sınıf tanımlamak için singleton terimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8267-197">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="b8267-198">Bu nedenle, tek bir sınıf için parametresiz Oluşturucu sınıfı sınıfının tek örneğine başlatacak.</span><span class="sxs-lookup"><span data-stu-id="b8267-198">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="b8267-199">Bir WMI sınıfının, nesne olan özellikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8267-199">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="b8267-200">Bu tür WMI sınıfı için kesin olarak belirlenmiş bir sınıf oluşturduğunuzda, katıştırılmış nesne özelliklerinin türleri için kesin olarak belirlenmiş sınıflar oluşturmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b8267-200">When you generate a strongly typed class for this type of WMI class, you should consider generating strongly typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="b8267-201">Bu, katıştırılmış nesnelere türü kesin belirlenmiş bir şekilde erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b8267-201">This will allow you to access the embedded objects in a strongly typed manner.</span></span> <span data-ttu-id="b8267-202">Üretilen kodun gömülü nesnenin türünü algılayamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b8267-202">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="b8267-203">Bu durumda, sorunu size bildirmek için, üretilen kodda bir açıklama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b8267-203">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="b8267-204">Sonra, özelliği üretilen diğer sınıfa yazmak için, üretilen kodu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8267-204">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="b8267-205">WMI'da, CIM_DATETIME veri türünün veri değeri belirli bir tarih ve saati veya bir zaman aralığını gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b8267-205">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="b8267-206">Veri değeri bir tarih ve saati gösteriyorsa, oluşturulan sınıftaki veri türü **DateTime**olur.</span><span class="sxs-lookup"><span data-stu-id="b8267-206">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="b8267-207">Veri değeri bir zaman aralığını gösterirse, oluşturulan sınıftaki veri türü **TimeSpan**olur.</span><span class="sxs-lookup"><span data-stu-id="b8267-207">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="b8267-208">Alternatif olarak, Visual Studio .NET içindeki Sunucu Gezgini Management uzantısını kullanarak kesin türü belirtilmiş bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8267-208">You can alternately generate a strongly typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="b8267-209">WMI hakkında daha fazla bilgi için Platform SDK 'Sı belgelerindeki **Windows Yönetim Araçları** konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="b8267-209">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b8267-210">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b8267-210">Examples</span></span>  
 <span data-ttu-id="b8267-211">Aşağıdaki komut, **root\cimv2** ad alanındaki **Win32_LogicalDisk** WMI sınıfı için C# kodunda yönetilen bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8267-211">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="b8267-212">Araç, yönetilen sınıfı kök içindeki c:\Disk.cs konumundaki kaynak dosyasına yazar **. CIMV2. Win32** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b8267-212">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="b8267-213">Aşağıdaki kod örneği, oluşturulan bir sınıfın programsal olarak nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b8267-213">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="b8267-214">İlk olarak, sınıfın bir örneği numaralandırılır ve yol yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="b8267-214">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="b8267-215">Ardından, başlatılacak oluşturulan sınıfın bir örneği bir WMI örneğiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b8267-215">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="b8267-216">`Process`, **Win32_Process** için oluşturulur ve `LogicalDisk` **root\cimv2** ad alanındaki **Win32_LogicalDisk** için oluşturulan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b8267-216">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8267-217">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8267-217">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="b8267-218">Araçlar</span><span class="sxs-lookup"><span data-stu-id="b8267-218">Tools</span></span>](index.md)
- [<span data-ttu-id="b8267-219">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="b8267-219">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
