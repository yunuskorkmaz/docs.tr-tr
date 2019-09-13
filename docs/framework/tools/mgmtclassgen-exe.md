---
title: Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce281398fe7ea3a280355a7b79cc7144aba256be
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894653"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="39676-102">Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="39676-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="39676-103">Yönetim Kesin Belirlenmiş Sınıf Üreticisi aracı, belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için erken bağlı yönetilen bir sınıfı hızlı bir şekilde üretmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="39676-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="39676-104">Oluşturulan sınıf, WMI sınıfının bir örneğine erişmek için yazmanız gereken kodu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="39676-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39676-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39676-105">Syntax</span></span>  
  
```console  
mgmtclassgen   
WMIClass [options]   
```  
  
|<span data-ttu-id="39676-106">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="39676-106">Argument</span></span>|<span data-ttu-id="39676-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39676-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="39676-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="39676-108">*WMIClass*</span></span>|<span data-ttu-id="39676-109">Kendisi için erken bağlı yönetilen bir sınıf oluşturulacak Windows Yönetim Araçları sınıfı.</span><span class="sxs-lookup"><span data-stu-id="39676-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="39676-110">Seçenek</span><span class="sxs-lookup"><span data-stu-id="39676-110">Option</span></span>|<span data-ttu-id="39676-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39676-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="39676-112">**/l** *dil*</span><span class="sxs-lookup"><span data-stu-id="39676-112">**/l**  *language*</span></span>|<span data-ttu-id="39676-113">Erken bağlı yönetilen sınıfın oluşturulacağı dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="39676-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="39676-114">Dil bağımsız değişkeni olarak csC#(; default), **vb** (Visual Basic), **mc** (C++) veya **js** (JScript) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39676-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="39676-115">**/m** *makine*</span><span class="sxs-lookup"><span data-stu-id="39676-115">**/m**  *machine*</span></span>|<span data-ttu-id="39676-116">WMI sınıfının bulunduğu, bağlanılacak bilgisayarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="39676-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="39676-117">Varsayılan, yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="39676-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="39676-118">**/n** *yolu*</span><span class="sxs-lookup"><span data-stu-id="39676-118">**/n**  *path*</span></span>|<span data-ttu-id="39676-119">WMI sınıfını içeren WMI ad alanına giden yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="39676-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="39676-120">Bu seçeneği belirtmezseniz, araç varsayılan **root\cimv2** ad alanında *WMIClass* için kod üretir.</span><span class="sxs-lookup"><span data-stu-id="39676-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="39676-121">**/o** *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="39676-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="39676-122">Yönetilen kod sınıfının içinde üretileceği .NET ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39676-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="39676-123">Bu seçeneği belirtmezseniz, araç ad alanını WMI ad alanını ve şema önekini kullanarak üretir.</span><span class="sxs-lookup"><span data-stu-id="39676-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="39676-124">Şema öneki, sınıf adının alt çizgi karakterinden önce gelen parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="39676-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="39676-125">Örneğin, **root\cimv2** ad alanındaki **Win32_OperatingSystem** sınıfı Için, araç sınıfı kök içinde oluşturur **. CIMV2. Win32**.</span><span class="sxs-lookup"><span data-stu-id="39676-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="39676-126">**/p** *dosya yolu*</span><span class="sxs-lookup"><span data-stu-id="39676-126">**/p**  *filepath*</span></span>|<span data-ttu-id="39676-127">Üretilen kodun içinde kaydedileceği dosyanın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="39676-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="39676-128">Bu seçeneği belirtmezseniz, araç dosyayı geçerli dizinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39676-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="39676-129">*WMIClass* bağımsız değişkenini kullanarak sınıfının oluşturduğu sınıf ve dosyayı adlandırır.</span><span class="sxs-lookup"><span data-stu-id="39676-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="39676-130">Sınıfın adı ve dosya, WMIClass adıyla aynıdır *.*</span><span class="sxs-lookup"><span data-stu-id="39676-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="39676-131">*WMIClass* bir alt çizgi karakteri içeriyorsa, araç alt çizgi karakterini izleyen sınıf adının bölümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="39676-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="39676-132">Örneğin, *WMIClass* adı **Win32_LogicalDisk**biçimindeyse, oluşturulan sınıf ve dosya "MantıksalDisk" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="39676-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="39676-133">Bir dosya zaten varsa, araç varolan dosyanın üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="39676-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="39676-134">**/PW** *parola*</span><span class="sxs-lookup"><span data-stu-id="39676-134">**/pw**  *password*</span></span>|<span data-ttu-id="39676-135">**/M** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak parolayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="39676-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="39676-136">**/u** *Kullanıcı adı*</span><span class="sxs-lookup"><span data-stu-id="39676-136">**/u**  *user name*</span></span>|<span data-ttu-id="39676-137">**/M** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak kullanıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39676-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="39676-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="39676-138">**/?**</span></span>|<span data-ttu-id="39676-139">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="39676-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39676-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39676-140">Remarks</span></span>  
 <span data-ttu-id="39676-141">Mgmtclassgen. exe <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="39676-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="39676-142">Bu nedenle, C#, Visual Basic ve JScript'ten başka yönetilen dillerde kod üretmek için, herhangi bir özel kod sağlayıcısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39676-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="39676-143">Üretilen sınıfların, kendisi için üretildikleri şemaya bağlı olduklarını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="39676-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="39676-144">Arka plandaki şema değişirse, şemada yapılan değişiklikleri yansıtmasını isterseniz, sınıfı yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39676-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="39676-145">Aşağıdaki tabloda, WMI Ortak Bilgi Modeli (CIM) türlerinin üretilmiş bir sınıftaki veri türleriyle nasıl eşleştiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="39676-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="39676-146">CIM türü</span><span class="sxs-lookup"><span data-stu-id="39676-146">CIM type</span></span>|<span data-ttu-id="39676-147">Oluşturulan sınıf içinde veri türü</span><span class="sxs-lookup"><span data-stu-id="39676-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="39676-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="39676-148">CIM_SINT8</span></span>|<span data-ttu-id="39676-149">**SByte**</span><span class="sxs-lookup"><span data-stu-id="39676-149">**SByte**</span></span>|  
|<span data-ttu-id="39676-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="39676-150">CIM_UINT8</span></span>|<span data-ttu-id="39676-151">**Bayt**</span><span class="sxs-lookup"><span data-stu-id="39676-151">**Byte**</span></span>|  
|<span data-ttu-id="39676-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="39676-152">CIM_SINT16</span></span>|<span data-ttu-id="39676-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="39676-153">**Int16**</span></span>|  
|<span data-ttu-id="39676-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="39676-154">CIM_UINT16</span></span>|<span data-ttu-id="39676-155">**Int16**</span><span class="sxs-lookup"><span data-stu-id="39676-155">**UInt16**</span></span>|  
|<span data-ttu-id="39676-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="39676-156">CIM_SINT32</span></span>|<span data-ttu-id="39676-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="39676-157">**Int32**</span></span>|  
|<span data-ttu-id="39676-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="39676-158">SIM_UINT32</span></span>|<span data-ttu-id="39676-159">**Int32**</span><span class="sxs-lookup"><span data-stu-id="39676-159">**UInt32**</span></span>|  
|<span data-ttu-id="39676-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="39676-160">CIM_SINT64</span></span>|<span data-ttu-id="39676-161">**Tutulamaz**</span><span class="sxs-lookup"><span data-stu-id="39676-161">**Int64**</span></span>|  
|<span data-ttu-id="39676-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="39676-162">CIM_UINT64</span></span>|<span data-ttu-id="39676-163">**Int64**</span><span class="sxs-lookup"><span data-stu-id="39676-163">**UInt64**</span></span>|  
|<span data-ttu-id="39676-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="39676-164">CIM_REAL32</span></span>|<span data-ttu-id="39676-165">**Sunuculu**</span><span class="sxs-lookup"><span data-stu-id="39676-165">**Single**</span></span>|  
|<span data-ttu-id="39676-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="39676-166">CIM_REAL64</span></span>|<span data-ttu-id="39676-167">**Çift**</span><span class="sxs-lookup"><span data-stu-id="39676-167">**Double**</span></span>|  
|<span data-ttu-id="39676-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="39676-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="39676-169">**Boole değeri**</span><span class="sxs-lookup"><span data-stu-id="39676-169">**Boolean**</span></span>|  
|<span data-ttu-id="39676-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="39676-170">CIM_String</span></span>|<span data-ttu-id="39676-171">**Dize**</span><span class="sxs-lookup"><span data-stu-id="39676-171">**String**</span></span>|  
|<span data-ttu-id="39676-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="39676-172">CIM_DATETIME</span></span>|<span data-ttu-id="39676-173">**DateTime** veya **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="39676-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="39676-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="39676-174">CIM_REFERENCE</span></span>|<span data-ttu-id="39676-175">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="39676-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="39676-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="39676-176">CIM_CHAR16</span></span>|<span data-ttu-id="39676-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="39676-177">**Char**</span></span>|  
|<span data-ttu-id="39676-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="39676-178">CIM_OBJECT</span></span>|<span data-ttu-id="39676-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="39676-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="39676-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="39676-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="39676-181">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="39676-181">**Object**</span></span>|  
|<span data-ttu-id="39676-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="39676-182">CIM_ARRAY</span></span>|<span data-ttu-id="39676-183">Yukarıda sözü edilen nesnelerin dizisi</span><span class="sxs-lookup"><span data-stu-id="39676-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="39676-184">Bir WMI sınıfı oluşturduğunuzda, aşağıdaki davranışlara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="39676-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="39676-185">Standart bir genel özelliğin veya yöntemin, varolan bir özellikle veya yöntemle aynı ada sahip olması olanaklıdır.</span><span class="sxs-lookup"><span data-stu-id="39676-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="39676-186">Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="39676-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="39676-187">Oluşturulan bir sınıftaki bir özellik veya yöntemin adının hedef programlama dilinde bir anahtar sözcük olması olanaklıdır.</span><span class="sxs-lookup"><span data-stu-id="39676-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="39676-188">Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="39676-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="39676-189">WMI'da, niteleyiciler bir sınıfı, örneği, özelliği veya yöntemi tanımlamak için bilgi içeren değiştiricilerdir.</span><span class="sxs-lookup"><span data-stu-id="39676-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="39676-190">WMI, oluşturulmuş bir sınıftaki bir özelliği tanımlamakta kullanılacak **Read**, **Write**ve **Key** gibi standart niteleyicileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="39676-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="39676-191">Örneğin, bir **okuma** niteleyicisi ile değiştirilen bir özellik yalnızca oluşturulan sınıfta bir özellik **Get** erişimcisi ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="39676-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="39676-192">**Okuma** niteleyicisi ile işaretlenen bir özelliğin Salt okunabilir olması amaçlandığından, bir **küme** erişimcisi tanımlı değildir.</span><span class="sxs-lookup"><span data-stu-id="39676-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="39676-193">Değerin yalnızca belirtilen izin verilen değerlere ayarlanabileceği göstermek için **Values** ve **ValueMaps** niteleyicilerine göre sayısal bir özellik değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="39676-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="39676-194">Bu **değerler** ve **ValueMaps** ile bir numaralandırma oluşturulur ve özellik sabit listesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="39676-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="39676-195">WMI, yalnızca bir örneği olabilecek bir sınıf tanımlamak için singleton terimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="39676-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="39676-196">Bu nedenle, tek bir sınıf için parametresiz Oluşturucu sınıfı sınıfının tek örneğine başlatacak.</span><span class="sxs-lookup"><span data-stu-id="39676-196">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="39676-197">Bir WMI sınıfının, nesne olan özellikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="39676-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="39676-198">Bu tür WMI sınıfı için kesin olarak belirlenmiş bir sınıf ürettiğinizde, gömülü nesne özellikleri türleri için kesin olarak belirlenmiş türler oluşturmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="39676-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="39676-199">Bu, gömülü nesnelere kesin olarak belirlenmiş bir şekilde erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="39676-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="39676-200">Üretilen kodun gömülü nesnenin türünü algılayamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="39676-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="39676-201">Bu durumda, sorunu size bildirmek için, üretilen kodda bir açıklama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39676-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="39676-202">Sonra, özelliği üretilen diğer sınıfa yazmak için, üretilen kodu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39676-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="39676-203">WMI'da, CIM_DATETIME veri türünün veri değeri belirli bir tarih ve saati veya bir zaman aralığını gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="39676-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="39676-204">Veri değeri bir tarih ve saati gösteriyorsa, oluşturulan sınıftaki veri türü **DateTime**olur.</span><span class="sxs-lookup"><span data-stu-id="39676-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="39676-205">Veri değeri bir zaman aralığını gösterirse, oluşturulan sınıftaki veri türü **TimeSpan**olur.</span><span class="sxs-lookup"><span data-stu-id="39676-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="39676-206">Alternatif olarak, Visual Studio .NET'te Sunucu Gezgini Yönetim Uzantısı'nı kullanarak, kesin olarak belirlenmiş bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39676-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="39676-207">WMI hakkında daha fazla bilgi için Platform SDK 'Sı belgelerindeki **Windows Yönetim Araçları** konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="39676-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="39676-208">Örnekler</span><span class="sxs-lookup"><span data-stu-id="39676-208">Examples</span></span>  
 <span data-ttu-id="39676-209">Aşağıdaki komut, **root\cimv2** ad alanındaki **Win32_LogicalDisk** WMI C# sınıfına yönelik kodda yönetilen bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39676-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="39676-210">Araç, yönetilen sınıfı kök içindeki c:\Disk.cs konumundaki kaynak dosyasına yazar **. CIMV2. Win32** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="39676-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="39676-211">Aşağıdaki kod örneği, oluşturulan bir sınıfın programsal olarak nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="39676-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="39676-212">İlk olarak, sınıfın bir örneği numaralandırılır ve yol yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="39676-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="39676-213">Ardından, başlatılacak oluşturulan sınıfın bir örneği bir WMI örneğiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39676-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="39676-214">`Process`, **Win32_Process** için oluşturulan sınıftır ve `LogicalDisk` **root\cimv2** ad alanındaki **Win32_LogicalDisk** için oluşturulan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="39676-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39676-215">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39676-215">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="39676-216">Araçlar</span><span class="sxs-lookup"><span data-stu-id="39676-216">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="39676-217">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="39676-217">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
