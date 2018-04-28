---
title: XML Dosyasını İşleme (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 86dae99f2d17a506a27cf491a76083df618ba27b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="fcbe5-102">XML Dosyasını İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcbe5-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="fcbe5-103">Derleyici kodunuzda belgeleri oluşturmak için etiketli her yapı için bir kimlik dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="fcbe5-104">(Kodunuzu etiketi hakkında daha fazla bilgi için bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) Kimlik dizesi, yapı benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="fcbe5-105">XML dosyasını işleme programlar karşılık gelen tanımlamak için bir kimlik dizesi kullanabilirsiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] meta veri/yansıma öğesi.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="fcbe5-106">XML dosyası kodunuzu hiyerarşik bir gösterimini değil; her öğe için oluşturulan kimliği düz bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="fcbe5-107">Kimlik dizeleri oluşturduğunda derleyici aşağıdaki kurallara uyan:</span><span class="sxs-lookup"><span data-stu-id="fcbe5-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="fcbe5-108">Hiçbir boşluk dizesi içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="fcbe5-109">Kimlik dizesi ilk bölümü, izleyen iki nokta ile tek bir karakter ile tanımlanmasını üye türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="fcbe5-110">Aşağıdaki üye türleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="fcbe5-111">Karakter</span><span class="sxs-lookup"><span data-stu-id="fcbe5-111">Character</span></span>|<span data-ttu-id="fcbe5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcbe5-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="fcbe5-113">N</span><span class="sxs-lookup"><span data-stu-id="fcbe5-113">N</span></span>|<span data-ttu-id="fcbe5-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="fcbe5-114">namespace</span></span><br /><br /> <span data-ttu-id="fcbe5-115">Belge açıklamaları için bir ad alanı ekleyemezsiniz, ancak bunları CREF başvurular yapabilirsiniz desteklendiği yerlerde.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="fcbe5-116">T</span><span class="sxs-lookup"><span data-stu-id="fcbe5-116">T</span></span>|<span data-ttu-id="fcbe5-117">Tür: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span><span class="sxs-lookup"><span data-stu-id="fcbe5-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="fcbe5-118">F</span><span class="sxs-lookup"><span data-stu-id="fcbe5-118">F</span></span>|<span data-ttu-id="fcbe5-119">alan: `Dim`</span><span class="sxs-lookup"><span data-stu-id="fcbe5-119">field: `Dim`</span></span>|  
|<span data-ttu-id="fcbe5-120">P</span><span class="sxs-lookup"><span data-stu-id="fcbe5-120">P</span></span>|<span data-ttu-id="fcbe5-121">Özellik: `Property` (varsayılan özellikleri dahil)</span><span class="sxs-lookup"><span data-stu-id="fcbe5-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="fcbe5-122">M</span><span class="sxs-lookup"><span data-stu-id="fcbe5-122">M</span></span>|<span data-ttu-id="fcbe5-123">yöntem: `Sub`, `Function`, `Declare`, `Operator`</span><span class="sxs-lookup"><span data-stu-id="fcbe5-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="fcbe5-124">E</span><span class="sxs-lookup"><span data-stu-id="fcbe5-124">E</span></span>|<span data-ttu-id="fcbe5-125">Olay: `Event`</span><span class="sxs-lookup"><span data-stu-id="fcbe5-125">event: `Event`</span></span>|  
|<span data-ttu-id="fcbe5-126">!</span><span class="sxs-lookup"><span data-stu-id="fcbe5-126">!</span></span>|<span data-ttu-id="fcbe5-127">Hata dizesi</span><span class="sxs-lookup"><span data-stu-id="fcbe5-127">error string</span></span><br /><br /> <span data-ttu-id="fcbe5-128">Dizenin geri kalanı hata hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="fcbe5-129">Visual Basic derleyici çözümlenemiyor bağlantılar için hata bilgilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="fcbe5-130">İkinci bölümü `String` ad alanı kökünde başlayan öğesi, tam adı.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="fcbe5-131">Öğesi, kendi kapsayan türlerini ve ad alanı adını noktalarla ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="fcbe5-132">Öğesinin adı nokta içeriyorsa, numara karakteriyle değiştirilir (#).</span><span class="sxs-lookup"><span data-stu-id="fcbe5-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="fcbe5-133">Öğe adını doğrudan bir numara işareti olduğunu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="fcbe5-134">Örneğin, tam adını `String` Oluşturucusu olacaktır `System.String.#ctor`.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="fcbe5-135">Yöntemi için bağımsız değişkeni varsa özellikleri ve yöntemleri için ayraç içinde bağımsız değişken listesi aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="fcbe5-136">Bağımsız değişkenler varsa, hiçbir parantez yok.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="fcbe5-137">Bağımsız değişkenler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-137">The arguments are separated by commas.</span></span> <span data-ttu-id="fcbe5-138">Her bağımsız değişkeni kodlama doğrudan nasıl içinde kodlanır izleyen bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] imza.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcbe5-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcbe5-139">Example</span></span>  
 <span data-ttu-id="fcbe5-140">Aşağıdaki kod kimliği için bir sınıf nasıl dizeleri gösterir ve üyeleri üretilir.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fcbe5-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcbe5-141">See Also</span></span>  
 [<span data-ttu-id="fcbe5-142">/doc</span><span class="sxs-lookup"><span data-stu-id="fcbe5-142">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="fcbe5-143">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fcbe5-143">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
