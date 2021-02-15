---
description: 'Hakkında daha fazla bilgi edinin: XML dosyası Işleme (Visual Basic)'
title: XML Dosyasını İşleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 2314e7dafbd747f9a19b73d06d71c73631e53861
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468401"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="277b3-103">XML Dosyasını İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="277b3-103">Processing the XML File (Visual Basic)</span></span>

<span data-ttu-id="277b3-104">Derleyici, kodunuzda belge oluşturmak için etiketlenmiş her yapı için bir KIMLIK dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="277b3-104">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="277b3-105">(Kodunuzu etiketleme hakkında daha fazla bilgi için bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md).) KIMLIK dizesi yapıyı benzersiz bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="277b3-105">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="277b3-106">XML dosyasını işleyen programlar, karşılık gelen .NET Framework meta veri/yansıma öğesini tanımlamak için KIMLIK dizesini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="277b3-106">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="277b3-107">XML dosyası, kodunuzun hiyerarşik bir temsili değildir; her öğe için oluşturulmuş KIMLIĞI olan düz bir liste.</span><span class="sxs-lookup"><span data-stu-id="277b3-107">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="277b3-108">Derleyici, KIMLIK dizelerini oluşturduğunda aşağıdaki kuralları sunar:</span><span class="sxs-lookup"><span data-stu-id="277b3-108">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="277b3-109">Dizeye boşluk yerleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="277b3-109">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="277b3-110">KIMLIK dizesinin ilk bölümü, tanımlanmakta olan üyenin türünü tanımlar, tek bir karakter ve iki nokta üst üste gelir.</span><span class="sxs-lookup"><span data-stu-id="277b3-110">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="277b3-111">Aşağıdaki üye türleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="277b3-111">The following member types are used.</span></span>  
  
|<span data-ttu-id="277b3-112">Karakter</span><span class="sxs-lookup"><span data-stu-id="277b3-112">Character</span></span>|<span data-ttu-id="277b3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="277b3-113">Description</span></span>|  
|---|---|  
|<span data-ttu-id="277b3-114">N</span><span class="sxs-lookup"><span data-stu-id="277b3-114">N</span></span>|<span data-ttu-id="277b3-115">ad alanı</span><span class="sxs-lookup"><span data-stu-id="277b3-115">namespace</span></span><br /><br /> <span data-ttu-id="277b3-116">Bir ad alanına belge açıklamaları ekleyemezsiniz, ancak bu kişilere, desteklenmiş olduğu durumlarda bu başvuruları yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="277b3-116">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="277b3-117">T</span><span class="sxs-lookup"><span data-stu-id="277b3-117">T</span></span>|<span data-ttu-id="277b3-118">Tür: `Class` , `Module` ,,, `Interface` `Structure` `Enum` , `Delegate`</span><span class="sxs-lookup"><span data-stu-id="277b3-118">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="277b3-119">F</span><span class="sxs-lookup"><span data-stu-id="277b3-119">F</span></span>|<span data-ttu-id="277b3-120">alanla `Dim`</span><span class="sxs-lookup"><span data-stu-id="277b3-120">field: `Dim`</span></span>|  
|<span data-ttu-id="277b3-121">P</span><span class="sxs-lookup"><span data-stu-id="277b3-121">P</span></span>|<span data-ttu-id="277b3-122">Özellik: `Property` (varsayılan özellikler dahil)</span><span class="sxs-lookup"><span data-stu-id="277b3-122">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="277b3-123">M</span><span class="sxs-lookup"><span data-stu-id="277b3-123">M</span></span>|<span data-ttu-id="277b3-124">Yöntem: `Sub` , `Function` ,, `Declare``Operator`</span><span class="sxs-lookup"><span data-stu-id="277b3-124">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="277b3-125">E</span><span class="sxs-lookup"><span data-stu-id="277b3-125">E</span></span>|<span data-ttu-id="277b3-126">olay `Event`</span><span class="sxs-lookup"><span data-stu-id="277b3-126">event: `Event`</span></span>|  
|<span data-ttu-id="277b3-127">!</span><span class="sxs-lookup"><span data-stu-id="277b3-127">!</span></span>|<span data-ttu-id="277b3-128">hata dizesi</span><span class="sxs-lookup"><span data-stu-id="277b3-128">error string</span></span><br /><br /> <span data-ttu-id="277b3-129">Dizenin geri kalanı hata hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="277b3-129">The rest of the string provides information about the error.</span></span> <span data-ttu-id="277b3-130">Visual Basic Derleyicisi çözümlenemeyen bağlantılar için hata bilgileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="277b3-130">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="277b3-131">Öğesinin ikinci bölümü, `String` ad alanının kökünden başlayarak öğenin tam nitelikli adıdır.</span><span class="sxs-lookup"><span data-stu-id="277b3-131">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="277b3-132">Öğenin adı, kapsayan tür (ler) ve ad alanı noktalarla ayrılır.</span><span class="sxs-lookup"><span data-stu-id="277b3-132">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="277b3-133">Öğenin adının kendisi noktalar içeriyorsa, bunlar sayı işaretiyle (#) değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="277b3-133">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="277b3-134">Hiçbir öğenin doğrudan adında numara işareti olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="277b3-134">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="277b3-135">Örneğin, oluşturucunun tam adı `String` olacaktır `System.String.#ctor` .</span><span class="sxs-lookup"><span data-stu-id="277b3-135">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="277b3-136">Özellikler ve yöntemler için, yöntem için bağımsız değişkenler varsa, parantez içine alınmış bağımsız değişken listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="277b3-136">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="277b3-137">Bağımsız değişken yoksa, parantezler yok.</span><span class="sxs-lookup"><span data-stu-id="277b3-137">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="277b3-138">Bağımsız değişkenler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="277b3-138">The arguments are separated by commas.</span></span> <span data-ttu-id="277b3-139">Her bağımsız değişkenin kodlaması, .NET Framework imzasında nasıl kodlandığını doğrudan izler.</span><span class="sxs-lookup"><span data-stu-id="277b3-139">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="277b3-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="277b3-140">Example</span></span>  

 <span data-ttu-id="277b3-141">Aşağıdaki kod, bir sınıfa ve üyelerine ait KIMLIK dizelerinin nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="277b3-141">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="277b3-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="277b3-142">See also</span></span>

- [<span data-ttu-id="277b3-143">-doc</span><span class="sxs-lookup"><span data-stu-id="277b3-143">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="277b3-144">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="277b3-144">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
