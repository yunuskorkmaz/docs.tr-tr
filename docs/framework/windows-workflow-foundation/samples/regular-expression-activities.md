---
title: Normal ifade etkinlikleri
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201016"
---
# <a name="regular-expression-activities"></a>Normal ifade etkinlikleri
Bu örnek normal ifade işlevselliğini kullanıma sunan bir etkinlik kümesini oluşturmak nasıl gösterir <xref:System.Text.RegularExpressions> ad alanı. Bu özel etkinlikler, bir iş akışı uygulama içinde kullanılabilir. Normal ifadeler hakkında daha fazla bilgi için bkz. [t:System.Text.RegularExpressions.Regex](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 Aşağıdaki tabloda, bu örnekte özel etkinlikler ayrıntıları.  
  
|Etkinlik|Açıklama|  
|--------------|-----------------|  
|IsMatch|Normal ifade giriş dizesinde bir eşleşme bulundu olup olmadığını belirtir.|  
|Eşleşmeler|Bir Giriş dizesinin normal bir ifadenin tüm örnekleri için arar ve başarılı tüm eşleşmelerin döndürür.|  
|Değiştir|Belirtilen bir Giriş dizesinin içinde belirtilen değiştirme dizesi bir normal ifade deseniyle eşleşen dizeleri değiştirir.|  
  
## <a name="ismatch"></a>IsMatch  
 `IsMatch` Özel etkinlik döndürür `true` varsa `Input` dize özelliği içinde belirtilen normal ifade bir eşleşme bulur `Pattern` özelliği. Etkinlik türetildiği <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yöntemi.  
  
 Aşağıdaki tablo, özellikler ve dönüş değeri açıklar `IsMatch` özel etkinlik.  
  
|Özellik ya da dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|Deseni (gerekli)|İle aramak için normal ifade.|  
|Giriş (gerekli)|Arama giriş dizesi.|  
|RegexOptions|Bit düzeyindeki OR kombinasyonudur [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) sabit listesi değerleri.|  
|Dönüş değeri|`true` Giriş sağlanan desende bir eşleşme bulduğunda; Aksi takdirde `false`.|  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `IsMatch` özel etkinlik.  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Eşleşmeler  
 `Matches` Özel etkinlik bir Giriş dizesinin normal bir ifadenin tüm örnekleri için arar ve başarılı tüm eşleşmelerin döndürür. Etkinlik türetildiği <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi.  
  
 Aşağıdaki tablo, özellikler ve dönüş değeri açıklar `IsMatch` özel etkinlik.  
  
|Özellik ya da dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|Deseni (gerekli)|İle aramak için normal ifade.|  
|Giriş (gerekli)|Arama giriş dizesi.|  
|RegexOptions|Bit düzeyindeki OR kombinasyonudur [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) sabit listesi değerleri.|  
|Dönüş Değeri|A <xref:System.Text.RegularExpressions.MatchCollection> , başarılı bir eşleşme koleksiyonunu içerir.|  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Matches` özel etkinlik.  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>Değiştir  
 `Replace` Özel etkinlik bir Giriş dizesinin arar ve bir dize ile belirtilen normal ifadeyle eşleşen tüm dizeleri değiştirir. Etkinlik türetildiği <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Replace%2A> yöntemi.  
  
 Aşağıdaki tablo, özellikler ve dönüş değeri açıklar `Replace` özel etkinlik.  
  
|Özellik ya da dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|Deseni (gerekli)|İle aramak için normal ifade.|  
|Giriş (gerekli)|Arama giriş dizesi.|  
|Değiştirme|Değişim dizesi.<br /><br /> Varsa bir `Replacement` belirtilirse, ardından `MatchEvaluator` özelliği yok sayılır. Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.|  
|MatchEvaluator|Her bir eşleştirmeyi inceler ve özgün eşleşen dizeyi veya bir değiştirme dizesi döndüren özel bir yöntem.<br /><br /> Varsa bir `Replacement` belirtilirse, ardından `MatchEvaluator` özelliği yok sayılır. Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.|  
|RegexOptions|Bit düzeyindeki OR kombinasyonudur [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) sabit listesi değerleri.|  
|Dönüş Değeri|A <xref:System.Text.RegularExpressions.MatchCollection> , başarılı bir eşleşme koleksiyonunu içerir.|  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Replace` özel etkinlik.  
  
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
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RegexActivities.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`