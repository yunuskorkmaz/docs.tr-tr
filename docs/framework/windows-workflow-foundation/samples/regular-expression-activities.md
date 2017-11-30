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
ms.openlocfilehash: c04b5c97feb7843a5120e3b2171e132526caa961
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="regular-expression-activities"></a><span data-ttu-id="aff6a-102">Normal ifade etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="aff6a-102">Regular Expression Activities</span></span>
<span data-ttu-id="aff6a-103">Bu örnek, normal ifade işlevselliğini kullanıma sunabilir etkinlikleri kümesi oluşturmak gösterilmiştir <xref:System.Text.RegularExpressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="aff6a-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="aff6a-104">Bu özel etkinlikler bir iş akışı uygulama içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-104">These custom activities can be used within a workflow application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="aff6a-105">Normal ifadeler bkz [t:System.Text.RegularExpressions.Regex](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="aff6a-105"> regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="aff6a-106">Aşağıdaki tabloda, bu örnekteki özel etkinlikler ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="aff6a-107">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="aff6a-107">Activity</span></span>|<span data-ttu-id="aff6a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff6a-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="aff6a-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="aff6a-109">IsMatch</span></span>|<span data-ttu-id="aff6a-110">Normal ifade bir girdi dizesindeki eşleşme olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="aff6a-111">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="aff6a-111">Matches</span></span>|<span data-ttu-id="aff6a-112">Normal bir ifade tüm oluşumları için giriş dizesi arar ve tüm başarılı eşleşenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="aff6a-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="aff6a-113">Değiştir</span><span class="sxs-lookup"><span data-stu-id="aff6a-113">Replace</span></span>|<span data-ttu-id="aff6a-114">Belirtilen giriş dizesi içinde belirtilen değiştirme dizesi ile bir normal ifade ile eşleşen dizelerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="aff6a-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="aff6a-115">IsMatch</span></span>  
 <span data-ttu-id="aff6a-116">`IsMatch` Özel etkinlik döndürür `true` varsa `Input` dize özelliği, belirtilen normal ifadede bir eşleşme bulur `Pattern` özelliği.</span><span class="sxs-lookup"><span data-stu-id="aff6a-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="aff6a-117">Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aff6a-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="aff6a-118">Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aff6a-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="aff6a-119">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="aff6a-119">Property or Return Value</span></span>|<span data-ttu-id="aff6a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff6a-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="aff6a-121">Desen (gerekli)</span><span class="sxs-lookup"><span data-stu-id="aff6a-121">Pattern (required)</span></span>|<span data-ttu-id="aff6a-122">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="aff6a-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="aff6a-123">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="aff6a-123">Input (required)</span></span>|<span data-ttu-id="aff6a-124">Aramak için giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="aff6a-124">The input string to search.</span></span>|  
|<span data-ttu-id="aff6a-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="aff6a-125">RegexOptions</span></span>|<span data-ttu-id="aff6a-126">Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="aff6a-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="aff6a-127">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="aff6a-127">Return value</span></span>|<span data-ttu-id="aff6a-128">`true`Giriş sağlanan desende bir eşleşme bulursa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="aff6a-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="aff6a-129">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aff6a-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="aff6a-130">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="aff6a-130">Matches</span></span>  
 <span data-ttu-id="aff6a-131">`Matches` Özel etkinlik normal bir ifade tüm oluşumları için giriş dizesi arar ve tüm başarılı eşleşenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="aff6a-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="aff6a-132">Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aff6a-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="aff6a-133">Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aff6a-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="aff6a-134">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="aff6a-134">Property or Return Value</span></span>|<span data-ttu-id="aff6a-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff6a-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="aff6a-136">Desen (gerekli)</span><span class="sxs-lookup"><span data-stu-id="aff6a-136">Pattern (required)</span></span>|<span data-ttu-id="aff6a-137">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="aff6a-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="aff6a-138">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="aff6a-138">Input (required)</span></span>|<span data-ttu-id="aff6a-139">Aramak için giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="aff6a-139">The input string to search.</span></span>|  
|<span data-ttu-id="aff6a-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="aff6a-140">RegexOptions</span></span>|<span data-ttu-id="aff6a-141">Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="aff6a-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="aff6a-142">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aff6a-142">Return Value</span></span>|<span data-ttu-id="aff6a-143">A <xref:System.Text.RegularExpressions.MatchCollection> başarılı eşleşmeleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="aff6a-144">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `Matches` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aff6a-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="aff6a-145">Değiştir</span><span class="sxs-lookup"><span data-stu-id="aff6a-145">Replace</span></span>  
 <span data-ttu-id="aff6a-146">`Replace` Özel etkinlik giriş dizesi arar ve bir dizeyle belirtilen normal ifadeyle eşleşen tüm dizelerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="aff6a-147">Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Replace%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aff6a-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="aff6a-148">Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `Replace` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aff6a-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="aff6a-149">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="aff6a-149">Property or Return Value</span></span>|<span data-ttu-id="aff6a-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff6a-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="aff6a-151">Desen (gerekli)</span><span class="sxs-lookup"><span data-stu-id="aff6a-151">Pattern (required)</span></span>|<span data-ttu-id="aff6a-152">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="aff6a-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="aff6a-153">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="aff6a-153">Input (required)</span></span>|<span data-ttu-id="aff6a-154">Aramak için giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="aff6a-154">The input string to search.</span></span>|  
|<span data-ttu-id="aff6a-155">Değiştirme</span><span class="sxs-lookup"><span data-stu-id="aff6a-155">Replacement</span></span>|<span data-ttu-id="aff6a-156">Değişim dizesi.</span><span class="sxs-lookup"><span data-stu-id="aff6a-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="aff6a-157">Varsa bir `Replacement` belirtilirse, sonra `MatchEvaluator` özelliği yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="aff6a-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="aff6a-158">Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aff6a-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="aff6a-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="aff6a-159">MatchEvaluator</span></span>|<span data-ttu-id="aff6a-160">Her eşleşme inceler ve özgün eşleşen dize veya bir değiştirme dizesi döndürür özel bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="aff6a-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="aff6a-161">Varsa bir `Replacement` belirtilirse, sonra `MatchEvaluator` özelliği yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="aff6a-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="aff6a-162">Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aff6a-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="aff6a-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="aff6a-163">RegexOptions</span></span>|<span data-ttu-id="aff6a-164">Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="aff6a-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="aff6a-165">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aff6a-165">Return Value</span></span>|<span data-ttu-id="aff6a-166">A <xref:System.Text.RegularExpressions.MatchCollection> başarılı eşleşmeleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="aff6a-167">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `Replace` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aff6a-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="aff6a-168">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="aff6a-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="aff6a-169">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RegexActivities.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="aff6a-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="aff6a-170">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="aff6a-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="aff6a-171">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="aff6a-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aff6a-172">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="aff6a-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aff6a-173">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="aff6a-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aff6a-174">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="aff6a-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aff6a-175">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="aff6a-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`