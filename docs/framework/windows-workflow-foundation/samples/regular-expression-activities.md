---
title: Normal ifade etkinlikleri
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509888"
---
# <a name="regular-expression-activities"></a><span data-ttu-id="9166e-102">Normal ifade etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="9166e-102">Regular Expression Activities</span></span>
<span data-ttu-id="9166e-103">Bu örnek normal ifade işlevselliğini kullanıma sunan bir etkinlik kümesini oluşturmak nasıl gösterir <xref:System.Text.RegularExpressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9166e-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="9166e-104">Bu özel etkinlikler, bir iş akışı uygulama içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9166e-104">These custom activities can be used within a workflow application.</span></span> <span data-ttu-id="9166e-105">Normal ifadeler hakkında daha fazla bilgi için bkz. [t:System.Text.RegularExpressions.Regex](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="9166e-105">For more information about regular expressions, see [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="9166e-106">Aşağıdaki tabloda, bu örnekte özel etkinlikler ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="9166e-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="9166e-107">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="9166e-107">Activity</span></span>|<span data-ttu-id="9166e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9166e-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9166e-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="9166e-109">IsMatch</span></span>|<span data-ttu-id="9166e-110">Normal ifade giriş dizesinde bir eşleşme bulundu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9166e-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="9166e-111">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="9166e-111">Matches</span></span>|<span data-ttu-id="9166e-112">Bir Giriş dizesinin normal bir ifadenin tüm örnekleri için arar ve başarılı tüm eşleşmelerin döndürür.</span><span class="sxs-lookup"><span data-stu-id="9166e-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="9166e-113">Değiştir</span><span class="sxs-lookup"><span data-stu-id="9166e-113">Replace</span></span>|<span data-ttu-id="9166e-114">Belirtilen bir Giriş dizesinin içinde belirtilen değiştirme dizesi bir normal ifade deseniyle eşleşen dizeleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9166e-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="9166e-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="9166e-115">IsMatch</span></span>  
 <span data-ttu-id="9166e-116">`IsMatch` Özel etkinlik döndürür `true` varsa `Input` dize özelliği içinde belirtilen normal ifade bir eşleşme bulur `Pattern` özelliği.</span><span class="sxs-lookup"><span data-stu-id="9166e-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="9166e-117">Etkinlik türetildiği <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9166e-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="9166e-118">Aşağıdaki tablo, özellikler ve dönüş değeri açıklar `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9166e-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="9166e-119">Özellik ya da dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9166e-119">Property or Return Value</span></span>|<span data-ttu-id="9166e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9166e-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9166e-121">Deseni (gerekli)</span><span class="sxs-lookup"><span data-stu-id="9166e-121">Pattern (required)</span></span>|<span data-ttu-id="9166e-122">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="9166e-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="9166e-123">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="9166e-123">Input (required)</span></span>|<span data-ttu-id="9166e-124">Arama giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="9166e-124">The input string to search.</span></span>|  
|<span data-ttu-id="9166e-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="9166e-125">RegexOptions</span></span>|<span data-ttu-id="9166e-126">Bit düzeyindeki OR kombinasyonudur [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="9166e-126">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="9166e-127">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9166e-127">Return value</span></span>|<span data-ttu-id="9166e-128">`true` Giriş sağlanan desende bir eşleşme bulduğunda; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="9166e-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="9166e-129">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9166e-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="9166e-130">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="9166e-130">Matches</span></span>  
 <span data-ttu-id="9166e-131">`Matches` Özel etkinlik bir Giriş dizesinin normal bir ifadenin tüm örnekleri için arar ve başarılı tüm eşleşmelerin döndürür.</span><span class="sxs-lookup"><span data-stu-id="9166e-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="9166e-132">Etkinlik türetildiği <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9166e-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="9166e-133">Aşağıdaki tablo, özellikler ve dönüş değeri açıklar `IsMatch` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9166e-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="9166e-134">Özellik ya da dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9166e-134">Property or Return Value</span></span>|<span data-ttu-id="9166e-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9166e-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9166e-136">Deseni (gerekli)</span><span class="sxs-lookup"><span data-stu-id="9166e-136">Pattern (required)</span></span>|<span data-ttu-id="9166e-137">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="9166e-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="9166e-138">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="9166e-138">Input (required)</span></span>|<span data-ttu-id="9166e-139">Arama giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="9166e-139">The input string to search.</span></span>|  
|<span data-ttu-id="9166e-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="9166e-140">RegexOptions</span></span>|<span data-ttu-id="9166e-141">Bit düzeyindeki OR kombinasyonudur [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="9166e-141">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="9166e-142">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9166e-142">Return Value</span></span>|<span data-ttu-id="9166e-143">A <xref:System.Text.RegularExpressions.MatchCollection> , başarılı bir eşleşme koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9166e-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="9166e-144">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Matches` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9166e-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="9166e-145">Değiştir</span><span class="sxs-lookup"><span data-stu-id="9166e-145">Replace</span></span>  
 <span data-ttu-id="9166e-146">`Replace` Özel etkinlik bir Giriş dizesinin arar ve bir dize ile belirtilen normal ifadeyle eşleşen tüm dizeleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9166e-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="9166e-147">Etkinlik türetildiği <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Replace%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9166e-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="9166e-148">Aşağıdaki tablo, özellikler ve dönüş değeri açıklar `Replace` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9166e-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="9166e-149">Özellik ya da dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9166e-149">Property or Return Value</span></span>|<span data-ttu-id="9166e-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9166e-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9166e-151">Deseni (gerekli)</span><span class="sxs-lookup"><span data-stu-id="9166e-151">Pattern (required)</span></span>|<span data-ttu-id="9166e-152">İle aramak için normal ifade.</span><span class="sxs-lookup"><span data-stu-id="9166e-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="9166e-153">Giriş (gerekli)</span><span class="sxs-lookup"><span data-stu-id="9166e-153">Input (required)</span></span>|<span data-ttu-id="9166e-154">Arama giriş dizesi.</span><span class="sxs-lookup"><span data-stu-id="9166e-154">The input string to search.</span></span>|  
|<span data-ttu-id="9166e-155">Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9166e-155">Replacement</span></span>|<span data-ttu-id="9166e-156">Değişim dizesi.</span><span class="sxs-lookup"><span data-stu-id="9166e-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="9166e-157">Varsa bir `Replacement` belirtilirse, ardından `MatchEvaluator` özelliği yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="9166e-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="9166e-158">Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9166e-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="9166e-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="9166e-159">MatchEvaluator</span></span>|<span data-ttu-id="9166e-160">Her bir eşleştirmeyi inceler ve özgün eşleşen dizeyi veya bir değiştirme dizesi döndüren özel bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="9166e-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="9166e-161">Varsa bir `Replacement` belirtilirse, ardından `MatchEvaluator` özelliği yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="9166e-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="9166e-162">Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9166e-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="9166e-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="9166e-163">RegexOptions</span></span>|<span data-ttu-id="9166e-164">Bit düzeyindeki OR kombinasyonudur [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="9166e-164">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="9166e-165">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9166e-165">Return Value</span></span>|<span data-ttu-id="9166e-166">A <xref:System.Text.RegularExpressions.MatchCollection> , başarılı bir eşleşme koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9166e-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="9166e-167">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Replace` özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9166e-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9166e-168">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9166e-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="9166e-169">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RegexActivities.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9166e-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="9166e-170">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="9166e-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9166e-171">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="9166e-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9166e-172">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="9166e-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9166e-173">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9166e-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9166e-174">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9166e-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9166e-175">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9166e-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`