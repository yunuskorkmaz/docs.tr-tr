---
title: "Yerelleştirme Öznitelikleri ve Yorumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a603c854d389076d0054a43ebeb26f19145fa8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="localization-attributes-and-comments"></a><span data-ttu-id="9d28d-102">Yerelleştirme Öznitelikleri ve Yorumlar</span><span class="sxs-lookup"><span data-stu-id="9d28d-102">Localization Attributes and Comments</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="9d28d-103">Yerelleştirme açıklamalarını özelliklerdir, içinde [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kaynak kod yerelleştirme için kurallar ve ipuçları sağlamak için geliştiriciler tarafından sağlanan,.</span><span class="sxs-lookup"><span data-stu-id="9d28d-103"> localization comments are properties, inside [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] source code, supplied by developers to provide rules and hints for localization.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="9d28d-104">Yerelleştirme açıklamalarını içeren iki bilgi kümesi: Yerelleştirme öznitelikleri ve serbest biçimli yerelleştirme açıklamalarını.</span><span class="sxs-lookup"><span data-stu-id="9d28d-104"> localization comments contain two sets of information: localizability attributes and free-form localization comments.</span></span> <span data-ttu-id="9d28d-105">Yerelleştirme öznitelikleri tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme hangi kaynakların yerelleştirilmesi belirtmek için API.</span><span class="sxs-lookup"><span data-stu-id="9d28d-105">Localizability attributes are used by the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Localization API to indicate which resources are to be localized.</span></span> <span data-ttu-id="9d28d-106">Serbest biçimli açıklamalar dahil etmek için uygulama yazarı istediği herhangi bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-106">Free-form comments are any information that the application author wants to include.</span></span>  
  

  
<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a><span data-ttu-id="9d28d-107">Yerelleştirme yorumları</span><span class="sxs-lookup"><span data-stu-id="9d28d-107">Localization Comments</span></span>  
 <span data-ttu-id="9d28d-108">Biçimlendirme uygulaması yazarları içindeki belirli öğeler için gereksinimleri olup olmadığını [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], metin uzunluğu, yazı tipi ailesi veya yazı tipi boyutu kısıtlamaları gibi çevirmenler açıklamaları ile bu bilgileri iletmek [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="9d28d-108">If markup application authors have requirements for specific elements in [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], such as constraints on text length, font family, or font size, they can convey this information to localizers with comments in the [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] code.</span></span> <span data-ttu-id="9d28d-109">Kaynak kodu açıklamaları ekleme işlemi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9d28d-109">The process for adding comments to source code is as follows:</span></span>  
  
1.  <span data-ttu-id="9d28d-110">Uygulama geliştiricisi yerelleştirme açıklamalarını ekler [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="9d28d-110">Application developer adds localization comments to [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] source code.</span></span>  
  
2.  <span data-ttu-id="9d28d-111">Derleme işlemi sırasında derleme, Yorumlar parçası çıkışı Şerit ya da tüm açıklamaları Şerit serbest biçimli yerelleştirme açıklamalarını bırakmak mı yoksa .proj dosyasında belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d28d-111">During the build process, you can specify in the .proj file whether to leave the free-form localization comments in the assembly, strip out part of the comments, or strip out all the comments.</span></span> <span data-ttu-id="9d28d-112">Çıkarılan yorumlar ayrı bir dosyada yer alır.</span><span class="sxs-lookup"><span data-stu-id="9d28d-112">The stripped-out comments are placed in a separate file.</span></span> <span data-ttu-id="9d28d-113">Seçeneğini kullanarak belirttiğiniz bir `LocalizationDirectivesToLocFile` etiketi, örneğin:</span><span class="sxs-lookup"><span data-stu-id="9d28d-113">You specify your option using a `LocalizationDirectivesToLocFile` tag, eg:</span></span>  
  
     <span data-ttu-id="9d28d-114">`<LocalizationDirectivesToLocFile>`*değeri*`</LocalizationDirectivesToLocFile>`</span><span class="sxs-lookup"><span data-stu-id="9d28d-114">`<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`</span></span>  
  
3.  <span data-ttu-id="9d28d-115">Atanabilir değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d28d-115">The values that can be assigned are:</span></span>  
  
    -   <span data-ttu-id="9d28d-116">**Hiçbiri** -hem açıklamaları ve öznitelikleri derleme içinde kalır ve ayrı bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d28d-116">**None** - Both comments and attributes stay inside the assembly and no separate file is generated.</span></span>  
  
    -   <span data-ttu-id="9d28d-117">**CommentsOnly** - derleme yalnızca açıklamalardan ve bunları ayrı bir LocFile içine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-117">**CommentsOnly** - Strips only the comments from the assembly and places them in the separate LocFile.</span></span>  
  
    -   <span data-ttu-id="9d28d-118">**Tüm** - açıklamaları ve öznitelikleri derlemesinden kaldırır ve bunları ayrı bir LocFile içine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-118">**All** - Strips both the comments and the attributes from the assembly and places them both in a separate LocFile.</span></span>  
  
4.  <span data-ttu-id="9d28d-119">Gelen yerelleştirilebilir kaynakları ayıklanırken [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], Yerelleştirme öznitelikleri tarafından kullanılır [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] yerelleştirme API'si.</span><span class="sxs-lookup"><span data-stu-id="9d28d-119">When localizable resources are extracted from [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], the localizability attributes are respected by the [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] Localization API.</span></span>  
  
5.  <span data-ttu-id="9d28d-120">Yalnızca serbest biçimli açıklamalar içeren yerelleştirme yorumları dosyaları daha sonraki bir zamanda yerelleştirme işlemi içine birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-120">Localization comment files, containing only free-form comments, are incorporated into the localization process at a later time.</span></span>  
  
 <span data-ttu-id="9d28d-121">Aşağıdaki örnek, yerelleştirme açıklama eklemek gösterilmiştir bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] dosyası.</span><span class="sxs-lookup"><span data-stu-id="9d28d-121">The following example shows how to add localization comments to a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file.</span></span>  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 <span data-ttu-id="9d28d-122">Önceki örnekte Localization.Attributes Yerelleştirme öznitelikleri ve Localization.Comments bölümü serbest biçimli açıklamalar bölüm içerir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-122">In the previous sample the Localization.Attributes section contains the localization attributes and the Localization.Comments section the free-form comments.</span></span> <span data-ttu-id="9d28d-123">Aşağıdaki tablolarda, öznitelikleri ve yorumları ve anlamları yerelleştiriciye gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-123">The following tables show the attributes and comments and their meaning to the localizer.</span></span>  
  
|<span data-ttu-id="9d28d-124">Yerelleştirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="9d28d-124">Localization attributes</span></span>|<span data-ttu-id="9d28d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d28d-125">Meaning</span></span>|  
|-----------------------------|-------------|  
|<span data-ttu-id="9d28d-126">$Content (değiştirilemeyen okunabilir metin)</span><span class="sxs-lookup"><span data-stu-id="9d28d-126">$Content (Unmodifiable Readable Text)</span></span>|<span data-ttu-id="9d28d-127">TextBlock öğesinin içeriği değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="9d28d-127">Contents of the TextBlock element cannot be modified.</span></span> <span data-ttu-id="9d28d-128">Çevirmenler "Microsoft" sözcüğünü değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d28d-128">Localizers cannot change the word "Microsoft".</span></span> <span data-ttu-id="9d28d-129">İçeriği yerelleştiriciye görünür (okunabilir) olur.</span><span class="sxs-lookup"><span data-stu-id="9d28d-129">The content is visible (Readable) to the localizer.</span></span> <span data-ttu-id="9d28d-130">İçerik kategorisi metindir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-130">The category of the content is text.</span></span>|  
|<span data-ttu-id="9d28d-131">FontFamily (değiştirilemeyen okunabilir)</span><span class="sxs-lookup"><span data-stu-id="9d28d-131">FontFamily (Unmodifiable Readable)</span></span>|<span data-ttu-id="9d28d-132">TextBlock öğesinin yazı tipi ailesi özelliği değiştirilemez, ancak yerelleştiriciye görünür olur.</span><span class="sxs-lookup"><span data-stu-id="9d28d-132">The font family property of the TextBlock element cannot be changed but it is visible to the localizer.</span></span>|  
  
|<span data-ttu-id="9d28d-133">Yerelleştirme serbest biçimli açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d28d-133">Localization free-form comments</span></span>|<span data-ttu-id="9d28d-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d28d-134">Meaning</span></span>|  
|--------------------------------------|-------------|  
|<span data-ttu-id="9d28d-135">$Content (ticari marka)</span><span class="sxs-lookup"><span data-stu-id="9d28d-135">$Content (Trademark)</span></span>|<span data-ttu-id="9d28d-136">Uygulama yazarı yerelleştiriciye TextBlock öğe içeriğinde bir ticari marka olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="9d28d-136">The application author tells the localizer that the content in the TextBlock element is a trademark.</span></span>|  
|<span data-ttu-id="9d28d-137">FontSize (ticari marka yazı tipi boyutu)</span><span class="sxs-lookup"><span data-stu-id="9d28d-137">FontSize (Trademark font size)</span></span>|<span data-ttu-id="9d28d-138">Uygulama yazarı yazı tipi boyutu özelliğinin standart ticari marka boyutunu izlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-138">The application author indicates that the font size property should follow the standard trademark size.</span></span>|  
  
### <a name="localizability-attributes"></a><span data-ttu-id="9d28d-139">Yerelleştirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="9d28d-139">Localizability Attributes</span></span>  
 <span data-ttu-id="9d28d-140">Çiftlerinin listesini Localization.Attributes bilgileri içerir: hedeflenen değer adını ve ilişkili yerelleştirme değerleri.</span><span class="sxs-lookup"><span data-stu-id="9d28d-140">The information in Localization.Attributes contains a list of pairs: the targeted value name and the associated localizability values.</span></span> <span data-ttu-id="9d28d-141">Hedef adı, bir özellik adı veya özel $Content adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-141">The target name can be a property name or the special $Content name.</span></span> <span data-ttu-id="9d28d-142">Bir özellik adı ise, hedeflenen özelliğinin değeri değerdir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-142">If it is a property name, the targeted value is the value of the property.</span></span> <span data-ttu-id="9d28d-143">$Content ise, hedef değer öğesi içeriktir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-143">If it is $Content, the target value is the content of the element.</span></span>  
  
 <span data-ttu-id="9d28d-144">Üç tür öznitelik vardır:</span><span class="sxs-lookup"><span data-stu-id="9d28d-144">There are three types of attributes:</span></span>  
  
-   <span data-ttu-id="9d28d-145">**Kategori**.</span><span class="sxs-lookup"><span data-stu-id="9d28d-145">**Category**.</span></span> <span data-ttu-id="9d28d-146">Bu, bir değer yerelleştirici araçtan değiştirilebilir olup olmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-146">This specifies whether a value should be modifiable from a localizer tool.</span></span> <span data-ttu-id="9d28d-147">Bkz: <xref:System.Windows.LocalizabilityAttribute.Category%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d28d-147">See <xref:System.Windows.LocalizabilityAttribute.Category%2A>.</span></span>  
  
-   <span data-ttu-id="9d28d-148">**Okunabilirlik**.</span><span class="sxs-lookup"><span data-stu-id="9d28d-148">**Readability**.</span></span> <span data-ttu-id="9d28d-149">Bu yerelleştirici aracın gerekip gerekmediğini belirten bir değer okuma (ve görüntüleme).</span><span class="sxs-lookup"><span data-stu-id="9d28d-149">This specifies whether a localizer tool should read (and display) a value.</span></span> <span data-ttu-id="9d28d-150">Bkz: <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d28d-150">See <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.</span></span>  
  
-   <span data-ttu-id="9d28d-151">**Modifiability'e göre**.</span><span class="sxs-lookup"><span data-stu-id="9d28d-151">**Modifiability**.</span></span> <span data-ttu-id="9d28d-152">Bu, yerelleştirici aracın bir değerin değiştirilmesine izin verip vermeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-152">This specifies whether a localizer tool allows a value to be modified.</span></span> <span data-ttu-id="9d28d-153">Bkz: <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d28d-153">See <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.</span></span>  
  
 <span data-ttu-id="9d28d-154">Bu öznitelikler, boşlukla ayrılmış herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-154">These attributes can be specified in any order delimited by a space.</span></span> <span data-ttu-id="9d28d-155">Yinelenen öznitelikler belirtilmesi durumunda, son özniteliğini eski olanları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9d28d-155">In case duplicate attributes are specified, the last attribute will override former ones.</span></span> <span data-ttu-id="9d28d-156">Örneğin, Localization.Attributes son değeri olduğundan = Modifiability'i Modifiable "Değiştirilemeyen değiştirilebilir" belirler.</span><span class="sxs-lookup"><span data-stu-id="9d28d-156">For example, Localization.Attributes = "Unmodifiable Modifiable" sets Modifiability to Modifiable because it is the last value.</span></span>  
  
 <span data-ttu-id="9d28d-157">Modifiability'e göre ve okunabilirliği niteliktedir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-157">Modifiability and Readability are self-explanatory.</span></span> <span data-ttu-id="9d28d-158">Kategori özniteliği metni çevirirken yerelleştiriciye yardım tanımlanmış kategorilerle sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d28d-158">The Category attribute provides predefined categories that help the localizer when translating text.</span></span> <span data-ttu-id="9d28d-159">Örneğin, metin, etiket ve başlık verin metin çevirme hakkında yerelleştiriciye bilgi kategoriler.</span><span class="sxs-lookup"><span data-stu-id="9d28d-159">Categories, such as, Text, Label, and Title give the localizer information about how to translate the text.</span></span> <span data-ttu-id="9d28d-160">Ayrıca özel kategoriye ayrılır: None, devralma, yoksay ve NeverLocalize.</span><span class="sxs-lookup"><span data-stu-id="9d28d-160">There are also special categories: None, Inherit, Ignore, and NeverLocalize.</span></span>  
  
 <span data-ttu-id="9d28d-161">Aşağıdaki tabloda özel kategoriler anlamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-161">The following table shows the meaning of the special categories.</span></span>  
  
|<span data-ttu-id="9d28d-162">Kategori</span><span class="sxs-lookup"><span data-stu-id="9d28d-162">Category</span></span>|<span data-ttu-id="9d28d-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d28d-163">Meaning</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="9d28d-164">Yok.</span><span class="sxs-lookup"><span data-stu-id="9d28d-164">None</span></span>|<span data-ttu-id="9d28d-165">Hedeflenen değer tanımlanmış bir kategorisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9d28d-165">Targeted value has no defined category.</span></span>|  
|<span data-ttu-id="9d28d-166">Devral</span><span class="sxs-lookup"><span data-stu-id="9d28d-166">Inherit</span></span>|<span data-ttu-id="9d28d-167">Hedeflenen değer kategorisinin üst öğesinden devralıyor.</span><span class="sxs-lookup"><span data-stu-id="9d28d-167">Targeted value inherits its category from its parent.</span></span>|  
|<span data-ttu-id="9d28d-168">Yoksay</span><span class="sxs-lookup"><span data-stu-id="9d28d-168">Ignore</span></span>|<span data-ttu-id="9d28d-169">Hedeflenen değer yerelleştirme işleminde göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-169">Targeted value is ignored in the localization process.</span></span> <span data-ttu-id="9d28d-170">Yoksay yalnızca geçerli değeri etkiler.</span><span class="sxs-lookup"><span data-stu-id="9d28d-170">Ignore affects only the current value.</span></span> <span data-ttu-id="9d28d-171">Alt düğümler etkilemez.</span><span class="sxs-lookup"><span data-stu-id="9d28d-171">It will not affect child nodes.</span></span>|  
|<span data-ttu-id="9d28d-172">NeverLocalize</span><span class="sxs-lookup"><span data-stu-id="9d28d-172">NeverLocalize</span></span>|<span data-ttu-id="9d28d-173">Geçerli değer yerelleştirilmiş olamaz.</span><span class="sxs-lookup"><span data-stu-id="9d28d-173">Current value cannot be localized.</span></span> <span data-ttu-id="9d28d-174">Bu kategori, bir öğenin gruplar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="9d28d-174">This category is inherited by the children of an element.</span></span>|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a><span data-ttu-id="9d28d-175">Yerelleştirme yorumları</span><span class="sxs-lookup"><span data-stu-id="9d28d-175">Localization Comments</span></span>  
 <span data-ttu-id="9d28d-176">Localization.Comments hedeflenen değeri ile ilgili serbest biçimli dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-176">Localization.Comments contains free-form strings concerning the targeted value.</span></span> <span data-ttu-id="9d28d-177">Uygulama geliştiricilerinin çevirmenler vermek için bilgi ekleyebileceğiniz uygulama metninin nasıl çevrilen hakkında ipuçları.</span><span class="sxs-lookup"><span data-stu-id="9d28d-177">Application developers can add information to give localizers hints about how the applications text should be translated.</span></span> <span data-ttu-id="9d28d-178">Açıklamaları biçimi çevrelenen "(") tarafından herhangi bir dize olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d28d-178">The format of the comments can be any string surrounded by "()".</span></span> <span data-ttu-id="9d28d-179">Kullanım '\\' kaçış karakterleri için.</span><span class="sxs-lookup"><span data-stu-id="9d28d-179">Use '\\' to escape characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d28d-180">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d28d-180">See Also</span></span>  
 [<span data-ttu-id="9d28d-181">WPF için genelleştirme</span><span class="sxs-lookup"><span data-stu-id="9d28d-181">Globalization for WPF</span></span>](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [<span data-ttu-id="9d28d-182">Bir düğme oluşturmak için otomatik düzenini kullanın</span><span class="sxs-lookup"><span data-stu-id="9d28d-182">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [<span data-ttu-id="9d28d-183">Bir kılavuz için otomatik düzenini kullanın</span><span class="sxs-lookup"><span data-stu-id="9d28d-183">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)  
 [<span data-ttu-id="9d28d-184">Bir uygulama yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="9d28d-184">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
