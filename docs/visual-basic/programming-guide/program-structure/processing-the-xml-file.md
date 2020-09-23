---
title: XML Dosyasını İşleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 9e12f6f5d86957a7f9aaea6047a79957fac8ce1e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072138"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="e54ae-102">XML Dosyasını İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e54ae-102">Processing the XML File (Visual Basic)</span></span>

<span data-ttu-id="e54ae-103">Derleyici, kodunuzda belge oluşturmak için etiketlenmiş her yapı için bir KIMLIK dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e54ae-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="e54ae-104">(Kodunuzu etiketleme hakkında daha fazla bilgi için bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md).) KIMLIK dizesi yapıyı benzersiz bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e54ae-104">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="e54ae-105">XML dosyasını işleyen programlar, karşılık gelen .NET Framework meta veri/yansıma öğesini tanımlamak için KIMLIK dizesini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e54ae-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="e54ae-106">XML dosyası, kodunuzun hiyerarşik bir temsili değildir; her öğe için oluşturulmuş KIMLIĞI olan düz bir liste.</span><span class="sxs-lookup"><span data-stu-id="e54ae-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="e54ae-107">Derleyici, KIMLIK dizelerini oluşturduğunda aşağıdaki kuralları sunar:</span><span class="sxs-lookup"><span data-stu-id="e54ae-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="e54ae-108">Dizeye boşluk yerleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="e54ae-108">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="e54ae-109">KIMLIK dizesinin ilk bölümü, tanımlanmakta olan üyenin türünü tanımlar, tek bir karakter ve iki nokta üst üste gelir.</span><span class="sxs-lookup"><span data-stu-id="e54ae-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="e54ae-110">Aşağıdaki üye türleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e54ae-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="e54ae-111">Karakter</span><span class="sxs-lookup"><span data-stu-id="e54ae-111">Character</span></span>|<span data-ttu-id="e54ae-112">Description</span><span class="sxs-lookup"><span data-stu-id="e54ae-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="e54ae-113">N</span><span class="sxs-lookup"><span data-stu-id="e54ae-113">N</span></span>|<span data-ttu-id="e54ae-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="e54ae-114">namespace</span></span><br /><br /> <span data-ttu-id="e54ae-115">Bir ad alanına belge açıklamaları ekleyemezsiniz, ancak bu kişilere, desteklenmiş olduğu durumlarda bu başvuruları yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e54ae-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="e54ae-116">T</span><span class="sxs-lookup"><span data-stu-id="e54ae-116">T</span></span>|<span data-ttu-id="e54ae-117">Tür: `Class` , `Module` ,,, `Interface` `Structure` `Enum` , `Delegate`</span><span class="sxs-lookup"><span data-stu-id="e54ae-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="e54ae-118">F</span><span class="sxs-lookup"><span data-stu-id="e54ae-118">F</span></span>|<span data-ttu-id="e54ae-119">alanla `Dim`</span><span class="sxs-lookup"><span data-stu-id="e54ae-119">field: `Dim`</span></span>|  
|<span data-ttu-id="e54ae-120">P</span><span class="sxs-lookup"><span data-stu-id="e54ae-120">P</span></span>|<span data-ttu-id="e54ae-121">Özellik: `Property` (varsayılan özellikler dahil)</span><span class="sxs-lookup"><span data-stu-id="e54ae-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="e54ae-122">M</span><span class="sxs-lookup"><span data-stu-id="e54ae-122">M</span></span>|<span data-ttu-id="e54ae-123">Yöntem: `Sub` , `Function` ,, `Declare``Operator`</span><span class="sxs-lookup"><span data-stu-id="e54ae-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="e54ae-124">E</span><span class="sxs-lookup"><span data-stu-id="e54ae-124">E</span></span>|<span data-ttu-id="e54ae-125">olay `Event`</span><span class="sxs-lookup"><span data-stu-id="e54ae-125">event: `Event`</span></span>|  
|<span data-ttu-id="e54ae-126">!</span><span class="sxs-lookup"><span data-stu-id="e54ae-126">!</span></span>|<span data-ttu-id="e54ae-127">hata dizesi</span><span class="sxs-lookup"><span data-stu-id="e54ae-127">error string</span></span><br /><br /> <span data-ttu-id="e54ae-128">Dizenin geri kalanı hata hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e54ae-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="e54ae-129">Visual Basic Derleyicisi çözümlenemeyen bağlantılar için hata bilgileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e54ae-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="e54ae-130">Öğesinin ikinci bölümü, `String` ad alanının kökünden başlayarak öğenin tam nitelikli adıdır.</span><span class="sxs-lookup"><span data-stu-id="e54ae-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="e54ae-131">Öğenin adı, kapsayan tür (ler) ve ad alanı noktalarla ayrılır.</span><span class="sxs-lookup"><span data-stu-id="e54ae-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="e54ae-132">Öğenin adının kendisi noktalar içeriyorsa, bunlar sayı işaretiyle (#) değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e54ae-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="e54ae-133">Hiçbir öğenin doğrudan adında numara işareti olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e54ae-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="e54ae-134">Örneğin, oluşturucunun tam adı `String` olacaktır `System.String.#ctor` .</span><span class="sxs-lookup"><span data-stu-id="e54ae-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="e54ae-135">Özellikler ve yöntemler için, yöntem için bağımsız değişkenler varsa, parantez içine alınmış bağımsız değişken listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e54ae-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="e54ae-136">Bağımsız değişken yoksa, parantezler yok.</span><span class="sxs-lookup"><span data-stu-id="e54ae-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="e54ae-137">Bağımsız değişkenler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="e54ae-137">The arguments are separated by commas.</span></span> <span data-ttu-id="e54ae-138">Her bağımsız değişkenin kodlaması, .NET Framework imzasında nasıl kodlandığını doğrudan izler.</span><span class="sxs-lookup"><span data-stu-id="e54ae-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e54ae-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="e54ae-139">Example</span></span>  

 <span data-ttu-id="e54ae-140">Aşağıdaki kod, bir sınıfa ve üyelerine ait KIMLIK dizelerinin nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e54ae-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e54ae-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e54ae-141">See also</span></span>

- [<span data-ttu-id="e54ae-142">-doc</span><span class="sxs-lookup"><span data-stu-id="e54ae-142">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="e54ae-143">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e54ae-143">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
