---
title: "x:Arguments Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb1f5986a0d9f9eb69ade0228925ec06164cee4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xarguments-directive"></a>x:Arguments Yönergesi
Paketler yapı değişkenleri XAML varsayılan olmayan Oluşturucusu nesne öğesi bildiriminde ya da bir fabrika yöntemi nesne bildirimi.  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>XAML öğesi kullanımı (varsayılan olmayan Oluşturucu)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML öğesi kullanımı (fabrika yöntemi)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Yedekleme varsayılan olmayan Oluşturucusu veya Fabrika yönteme iletilecek bağımsız değişkenleri belirtin bir veya daha fazla nesne öğeleri.<br /><br /> Tipik kullanım gerçek bağımsız değişken değerleri belirtmek için nesne öğeleri başlatma metinde kullanmaktır. Örnekler bölümüne bakın.<br /><br /> Öğelerin sırasını önemlidir. XAML türleri sırayla türlerinin eşleşmesi gerekir ve yedekleme Oluşturucusu veya Fabrika yöntemi aşırı yüklemesini sırasını yazın.|  
|`methodName`|Herhangi bir işlem Fabrika yöntemin adını `x:Arguments` bağımsız değişkenler.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:FactoryMethod`kapsam ve davranışını değiştirebilirsiniz nerede `x:Arguments` uygular.  
  
 Öyle değilse `x:FactoryMethod` belirtilirse, `x:Arguments` yedekleme oluşturucular alternatif (varsayılan olmayan) imzalar için geçerlidir.  
  
 Varsa `x:FactoryMethod` belirtilirse, `x:Arguments` bir adlandırılmış yöntemi aşırı için geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
 XAML 2006 varsayılan olmayan başlatma başlatma metin aracılığıyla destekleyebilir. Ancak, bir başlatma metin oluşturma teknik pratik uygulamasının sınırlıdır. Başlatma metin tek bir metin dizesi kabul edilir; Bu nedenle, özel bilgiler öğeleri ve özel sınırlayıcıları dizesinden ayrıştıramıyor oluşturma davranışı için tür dönüştürücüsünü tanımlanmadıkça yalnızca tek bir parametre başlatma için özelliğini ekler. Ayrıca, nesne mantığı potansiyel olarak doğru bir dize dışında temelleri işleme için belirli bir XAML Ayrıştırıcıyı ait yerel varsayılan türü dönüştürücü metindir.  
  
 `x:Arguments` XAML kullanımı tipik herkese açık özellik öğesi kullanımı yönerge biçimlendirme içeren nesne öğenin türü başvurmuyor olmadığından değil. Gibi diğer yönergeleri benzer daha fazla `x:Code` burada öğesi demarks içinde işaretleme kabul varsayılandan gibi alt içeriği için bir aralığı. Bu durumda, her nesne öğesi XAML tür XAML ayrıştırıcıları göre hangi belirli Oluşturucusu fabrika yöntemi imza belirlemek için kullanılan bağımsız değişken türleri hakkında bilgi iletişim kuran bir `x:Arguments` kullanım başvurmak çalışıyor.  
  
 `x:Arguments`bir nesne öğesi için yapılandırılan herhangi diğer özellik öğelerinin, içerik, iç metni veya başlatma dizeleri nesne öğesinin gelmelidir. İçinde nesne öğelerin `x:Arguments` öznitelikleri ve başlatma dizeleri XAML türü ve yedekleme Oluşturucusu veya Fabrika yöntemi tarafından izin verildiği şekilde içerebilir. Nesne veya bağımsız değişkenler için özel XAML türler veya aksi takdirde varsayılan XAML ad uzayı dışında kurulan önek eşlemeleri başvurarak XAML türlerini belirtebilirsiniz.  
  
 XAML işlemcileri bağımsız değişkenleri nasıl belirtilen belirlemek için aşağıdaki kılavuzları kullanın `x:Arguments` bir nesne oluşturmak için kullanılmalıdır. Varsa `x:FactoryMethod` belirtilirse, bilgi karşılaştırıldığı belirtilen `x:FactoryMethod` (unutmayın değerini `x:FactoryMethod` yöntem adı ve adlandırılmış yöntemi aşırı olabilir. Varsa `x:FactoryMethod` belirtilmezse, bilgi nesnesinin tüm ortak oluşturucu aşırı kümesine karşılaştırılan. XAML işleme mantığı sonra parametrelerin sayısı karşılaştırır ve eşleşen parametre ile aşırı seçer. Birden fazla eşleşme varsa XAML işlemci sağlanan nesne öğeleri XAML türlerine göre parametre türlerini karşılaştırmanız gerekir. XAML işlemci davranış hala birden fazla eşleşme varsa, tanımlanmamıştır. Varsa bir `x:FactoryMethod` belirtildi, ancak yöntem çözümlenemiyor, XAML işlemci bir özel durum oluşturması gerekir.  
  
 XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik olarak mümkün değildir. Ancak, bu ne aksi başlatma metin ve tür dönüştürücüleri yapılabilir ötesinde hiçbir özellikleri sağlar ve bu sözdiziminin kullanıldığı XAML 2009 fabrika yöntemi özellikleri tasarım amacı değil.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, varsayılan olmayan bir oluşturucu imza sonra XAML kullanımını gösterir `x:Arguments` Bu imza erişir.  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 Aşağıdaki örnek, bir hedef fabrika yöntemi imzası sonra XAML kullanımını gösterir `x:Arguments` Bu imza erişir.  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
