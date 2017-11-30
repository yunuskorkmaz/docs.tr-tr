---
title: "Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cb30972e2b49a7005749f57c0223b9fa493cde52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a><span data-ttu-id="1fde7-102">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="1fde7-102">Differences Between Properties and Variables in Visual Basic</span></span>
<span data-ttu-id="1fde7-103">Değişkenlerin ve özelliklerin erişebilmeniz için değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1fde7-103">Variables and properties both represent values that you can access.</span></span> <span data-ttu-id="1fde7-104">Ancak, depolama ve uygulama farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="1fde7-104">However, there are differences in storage and implementation.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="1fde7-105">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1fde7-105">Variables</span></span>  
 <span data-ttu-id="1fde7-106">A *değişkeni* doğrudan bellek konumuna karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1fde7-106">A *variable* corresponds directly to a memory location.</span></span> <span data-ttu-id="1fde7-107">Bir tek bildirimi deyimi sahip bir değişken tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1fde7-107">You define a variable with a single declaration statement.</span></span> <span data-ttu-id="1fde7-108">Bir değişken olabilir bir *yerel değişken*yordam içindeki ve bu yordam yalnızca içinde kullanılabilir tanımlanan veya olabilir bir *üye değişkeni*, bir modül, sınıf veya yapı ancak içindeki tüm tanımlı yordam.</span><span class="sxs-lookup"><span data-stu-id="1fde7-108">A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure.</span></span> <span data-ttu-id="1fde7-109">Üye değişkeni olarak da adlandırılır bir *alan*.</span><span class="sxs-lookup"><span data-stu-id="1fde7-109">A member variable is also called a *field*.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1fde7-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1fde7-110">Properties</span></span>  
 <span data-ttu-id="1fde7-111">A *özelliği* modülü, sınıf veya yapı tanımlı bir veri öğesi.</span><span class="sxs-lookup"><span data-stu-id="1fde7-111">A *property* is a data element defined on a module, class, or structure.</span></span> <span data-ttu-id="1fde7-112">Kod bloğu arasında özelliğiyle tanımladığınız `Property` ve `End Property` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1fde7-112">You define a property with a code block between the `Property` and `End Property` statements.</span></span> <span data-ttu-id="1fde7-113">Kod bloğunu içeren bir `Get` yordamı, bir `Set` yordam veya her ikisi de.</span><span class="sxs-lookup"><span data-stu-id="1fde7-113">The code block contains a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="1fde7-114">Bu yordamları adlı *özellik yordamları* veya *özellik erişimcisi*.</span><span class="sxs-lookup"><span data-stu-id="1fde7-114">These procedures are called *property procedures* or *property accessors*.</span></span> <span data-ttu-id="1fde7-115">Alma veya özelliğin değerini depolama yanı sıra, ayrıca bir erişim sayaç güncelleştirme gibi özel eylemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fde7-115">In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="1fde7-116">Farkları</span><span class="sxs-lookup"><span data-stu-id="1fde7-116">Differences</span></span>  
 <span data-ttu-id="1fde7-117">Aşağıdaki tabloda, değişkenler ve özellikleri arasında önemli bazı farklar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1fde7-117">The following table shows some important differences between variables and properties.</span></span>  
  
|<span data-ttu-id="1fde7-118">Fark noktası</span><span class="sxs-lookup"><span data-stu-id="1fde7-118">Point of difference</span></span>|<span data-ttu-id="1fde7-119">Değişken</span><span class="sxs-lookup"><span data-stu-id="1fde7-119">Variable</span></span>|<span data-ttu-id="1fde7-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="1fde7-120">Property</span></span>|  
|-------------------------|--------------|--------------|  
|<span data-ttu-id="1fde7-121">Bildirim</span><span class="sxs-lookup"><span data-stu-id="1fde7-121">Declaration</span></span>|<span data-ttu-id="1fde7-122">Tek bildirimi deyimi</span><span class="sxs-lookup"><span data-stu-id="1fde7-122">Single declaration statement</span></span>|<span data-ttu-id="1fde7-123">Kod bloğu deyimlerinde dizi</span><span class="sxs-lookup"><span data-stu-id="1fde7-123">Series of statements in a code block</span></span>|  
|<span data-ttu-id="1fde7-124">Uygulama</span><span class="sxs-lookup"><span data-stu-id="1fde7-124">Implementation</span></span>|<span data-ttu-id="1fde7-125">Tek bir depolama konumu</span><span class="sxs-lookup"><span data-stu-id="1fde7-125">Single storage location</span></span>|<span data-ttu-id="1fde7-126">Yürütülebilir kod (özellik yordamları)</span><span class="sxs-lookup"><span data-stu-id="1fde7-126">Executable code (property procedures)</span></span>|  
|<span data-ttu-id="1fde7-127">Depolama</span><span class="sxs-lookup"><span data-stu-id="1fde7-127">Storage</span></span>|<span data-ttu-id="1fde7-128">Doğrudan değişkenin değeriyle ilişkili</span><span class="sxs-lookup"><span data-stu-id="1fde7-128">Directly associated with variable's value</span></span>|<span data-ttu-id="1fde7-129">Genellikle özelliğin içeren sınıf veya modülü dışında kullanılamaz iç depolama alanına sahip</span><span class="sxs-lookup"><span data-stu-id="1fde7-129">Typically has internal storage not available outside the property's containing class or module</span></span><br /><br /> <span data-ttu-id="1fde7-130">Özelliğin değeri saklanan bir öğe var olmayabilir veya olabilir <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fde7-130">Property's value might or might not exist as a stored element <sup>1</sup></span></span>|  
|<span data-ttu-id="1fde7-131">Yürütülebilir kod</span><span class="sxs-lookup"><span data-stu-id="1fde7-131">Executable code</span></span>|<span data-ttu-id="1fde7-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="1fde7-132">None</span></span>|<span data-ttu-id="1fde7-133">En az bir yordam olmalıdır</span><span class="sxs-lookup"><span data-stu-id="1fde7-133">Must have at least one procedure</span></span>|  
|<span data-ttu-id="1fde7-134">Okuma ve yazma erişimi</span><span class="sxs-lookup"><span data-stu-id="1fde7-134">Read and write access</span></span>|<span data-ttu-id="1fde7-135">Okuma/yazma veya salt okunur</span><span class="sxs-lookup"><span data-stu-id="1fde7-135">Read/write or read-only</span></span>|<span data-ttu-id="1fde7-136">Okuma/yazma, salt okunur veya salt yazılır</span><span class="sxs-lookup"><span data-stu-id="1fde7-136">Read/write, read-only, or write-only</span></span>|  
|<span data-ttu-id="1fde7-137">(Ek olarak kabul etme veya değer döndürme) özel eylemler</span><span class="sxs-lookup"><span data-stu-id="1fde7-137">Custom actions (in addition to accepting or returning value)</span></span>|<span data-ttu-id="1fde7-138">Mümkün değil</span><span class="sxs-lookup"><span data-stu-id="1fde7-138">Not possible</span></span>|<span data-ttu-id="1fde7-139">Ayarlama veya özellik değeri alınırken bir parçası olarak gerçekleştirilebilir</span><span class="sxs-lookup"><span data-stu-id="1fde7-139">Can be performed as part of setting or retrieving property value</span></span>|  
  
 <span data-ttu-id="1fde7-140"><sup>1</sup> bir değişken depolama doğrudan tek bir öğe için bir özelliğin değerini gelmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="1fde7-140"><sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage.</span></span> <span data-ttu-id="1fde7-141">Depolama kolaylık veya güvenlik için parçalara bölmek veya değeri şifreli biçimde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="1fde7-141">The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form.</span></span> <span data-ttu-id="1fde7-142">Bu gibi durumlarda `Get` yordamı parçaları bir araya getirmek mi depolanan değer şifresini çözmek ve `Set` yordam yeni değer şifrelemek veya bağlı depolama alanına bölme.</span><span class="sxs-lookup"><span data-stu-id="1fde7-142">In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage.</span></span> <span data-ttu-id="1fde7-143">Bir özellik değeri, bu durumda kısa ömürlü, gün, saat gibi olabilir `Get` yordamı hesaplamak, anında özelliği her eriştiğinizde.</span><span class="sxs-lookup"><span data-stu-id="1fde7-143">A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fde7-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1fde7-144">See Also</span></span>  
 [<span data-ttu-id="1fde7-145">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="1fde7-145">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="1fde7-146">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1fde7-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="1fde7-147">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="1fde7-147">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="1fde7-148">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="1fde7-148">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="1fde7-149">Nasıl yapılır: özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="1fde7-149">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="1fde7-150">Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="1fde7-150">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="1fde7-151">Nasıl yapılır: bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="1fde7-151">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="1fde7-152">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="1fde7-152">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="1fde7-153">Nasıl yapılır: bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="1fde7-153">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="1fde7-154">Nasıl yapılır: bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="1fde7-154">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
