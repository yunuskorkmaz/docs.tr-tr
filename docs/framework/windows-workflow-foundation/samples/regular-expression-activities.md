---
title: Normal ifade etkinlikleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: edeb55f25abf9e6f22ebfe1d0ea63eb07ba0f203
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-activities"></a><span data-ttu-id="5b55e-102">Normal ifade etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="5b55e-102">Regular Expression Activities</span></span>
<span data-ttu-id="5b55e-103">Bu örnek, normal ifade işlevselliğini kullanıma sunabilir etkinlikleri kümesi oluşturmak gösterilmiştir <xref:System.Text.RegularExpressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5b55e-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="5b55e-104">Bu özel etkinlikler bir iş akışı uygulama içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-104">These custom activities can be used within a workflow application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5b55e-105">Normal ifadeler bkz [t:System.Text.RegularExpressions.Regex](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="5b55e-105"> regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="5b55e-106">Aşağıdaki tabloda, bu örnekteki özel etkinlikler ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="5b55e-107">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="5b55e-107">Activity</span></span>|<span data-ttu-id="5b55e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b55e-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5b55e-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="5b55e-109">IsMatch</span></span>|<span data-ttu-id="5b55e-110">Normal ifade bir girdi dizesindeki eşleşme olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="5b55e-111">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="5b55e-111">Matches</span></span>|<span data-ttu-id="5b55e-112">Normal bir ifade tüm oluşumları için giriş dizesi arar ve tüm başarılı eşleşenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b55e-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="5b55e-113">Değiştir</span><span class="sxs-lookup"><span data-stu-id="5b55e-113">Replace</span></span>|<span data-ttu-id="5b55e-114">Belirtilen giriş dizesi içinde belirtilen değiştirme dizesi ile bir normal ifade ile eşleşen dizelerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="5b55e-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="5b55e-115">IsMatch</span></span>  
 <span data-ttu-id="5b55e-116">`IsMatch` Özel etkinlik döndürür `true` varsa `Input` dize özelliği, belirtilen normal ifadede bir eşleşme bulur `Pattern` özelliği.</span><span class="sxs-lookup"><span data-stu-id="5b55e-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="5b55e-117">Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b55e-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="5b55e-118">Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5b55e-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="5b55e-119">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5b55e-119">Property or Return Value</span></span>|<span data-ttu-id="5b55e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b55e-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="5b55e-121">Desen (gerekli)</span><span class="sxs-lookup"><span data-stu-id="5b55e-121">Pattern (required)</span></span>|<span data-ttu-id="5b55e-122">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="5b55e-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="5b55e-123">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="5b55e-123">Input (required)</span></span>|<span data-ttu-id="5b55e-124">Aramak için giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="5b55e-124">The input string to search.</span></span>|  
|<span data-ttu-id="5b55e-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="5b55e-125">RegexOptions</span></span>|<span data-ttu-id="5b55e-126">Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="5b55e-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="5b55e-127">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5b55e-127">Return value</span></span>|<span data-ttu-id="5b55e-128">`true`Giriş sağlanan desende bir eşleşme bulursa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="5b55e-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="5b55e-129">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5b55e-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="5b55e-130">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="5b55e-130">Matches</span></span>  
 <span data-ttu-id="5b55e-131">`Matches` Özel etkinlik normal bir ifade tüm oluşumları için giriş dizesi arar ve tüm başarılı eşleşenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b55e-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="5b55e-132">Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b55e-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="5b55e-133">Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5b55e-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="5b55e-134">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5b55e-134">Property or Return Value</span></span>|<span data-ttu-id="5b55e-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b55e-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="5b55e-136">Desen (gerekli)</span><span class="sxs-lookup"><span data-stu-id="5b55e-136">Pattern (required)</span></span>|<span data-ttu-id="5b55e-137">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="5b55e-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="5b55e-138">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="5b55e-138">Input (required)</span></span>|<span data-ttu-id="5b55e-139">Aramak için giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="5b55e-139">The input string to search.</span></span>|  
|<span data-ttu-id="5b55e-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="5b55e-140">RegexOptions</span></span>|<span data-ttu-id="5b55e-141">Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="5b55e-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="5b55e-142">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b55e-142">Return Value</span></span>|<span data-ttu-id="5b55e-143">A <xref:System.Text.RegularExpressions.MatchCollection> başarılı eşleşmeleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="5b55e-144">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `Matches` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5b55e-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="5b55e-145">Değiştir</span><span class="sxs-lookup"><span data-stu-id="5b55e-145">Replace</span></span>  
 <span data-ttu-id="5b55e-146">`Replace` Özel etkinlik giriş dizesi arar ve bir dizeyle belirtilen normal ifadeyle eşleşen tüm dizelerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="5b55e-147">Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Replace%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b55e-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="5b55e-148">Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `Replace` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5b55e-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="5b55e-149">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5b55e-149">Property or Return Value</span></span>|<span data-ttu-id="5b55e-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b55e-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="5b55e-151">Desen (gerekli)</span><span class="sxs-lookup"><span data-stu-id="5b55e-151">Pattern (required)</span></span>|<span data-ttu-id="5b55e-152">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="5b55e-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="5b55e-153">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="5b55e-153">Input (required)</span></span>|<span data-ttu-id="5b55e-154">Aramak için giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="5b55e-154">The input string to search.</span></span>|  
|<span data-ttu-id="5b55e-155">Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5b55e-155">Replacement</span></span>|<span data-ttu-id="5b55e-156">Değişim dizesi.</span><span class="sxs-lookup"><span data-stu-id="5b55e-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="5b55e-157">Varsa bir `Replacement` belirtilirse, sonra `MatchEvaluator` özelliği yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="5b55e-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="5b55e-158">Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b55e-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="5b55e-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="5b55e-159">MatchEvaluator</span></span>|<span data-ttu-id="5b55e-160">Her eşleşme inceler ve özgün eşleşen dize veya bir değiştirme dizesi döndürür özel bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="5b55e-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="5b55e-161">Varsa bir `Replacement` belirtilirse, sonra `MatchEvaluator` özelliği yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="5b55e-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="5b55e-162">Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b55e-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="5b55e-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="5b55e-163">RegexOptions</span></span>|<span data-ttu-id="5b55e-164">Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="5b55e-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="5b55e-165">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b55e-165">Return Value</span></span>|<span data-ttu-id="5b55e-166">A <xref:System.Text.RegularExpressions.MatchCollection> başarılı eşleşmeleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="5b55e-167">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `Replace` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5b55e-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5b55e-168">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5b55e-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="5b55e-169">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RegexActivities.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5b55e-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="5b55e-170">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5b55e-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5b55e-171">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5b55e-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5b55e-172">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b55e-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5b55e-173">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5b55e-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5b55e-174">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5b55e-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b55e-175">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5b55e-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`  
  
## <a name="see-also"></a><span data-ttu-id="5b55e-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b55e-176">See Also</span></span>
