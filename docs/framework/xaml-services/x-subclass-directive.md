---
title: x:Subclass Yönergesi
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: 850fe8acf9e47149bd385e78b30e04ba77d7a8b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140796"
---
# <a name="xsubclass-directive"></a>x:Subclass Yönergesi
XAML biçimlendirmesi derleme davranışını değiştiren olduğunda `x:Class` de sağlanır. Temel alan bir parçalı sınıf oluşturmak yerine `x:Class`, sağlanan `x:Class` Ara bir sınıf olarak oluşturulur ve ardından sağlanan türetilmiş sınıfınızın temel beklenen `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`namespace`|İsteğe bağlı. İçeren bir CLR ad alanını belirtir `classname`. Varsa `namespace` belirtilirse, nokta (.) ayıran `namespace` ve `classname`.|  
|`classname`|Gerekli. Yüklenen XAML ve kod arka plan için bu XAML bağlanan kısmi sınıf CLR adını belirtir. Açıklamalara bakın.|  
|`subclassNamespace`|İsteğe bağlı. Farklı olabilir `namespace` , her ad alanı diğer çözebilirsiniz. İçeren bir CLR ad alanını belirtir `subclassName`. Varsa `subclassName` belirtilirse, nokta (.) ayıran `subclassNamespace` ve `subclassName`.|  
|`subclassName`|Gerekli. Alt CLR adını belirtir.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 [x: Class yönergesi](x-class-directive.md) da aynı nesne üzerinde sağlanmalıdır ve o nesnenin XAML üretim kök öğesi olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Subclass` Kullanım, öncelikle kısmi sınıf bildirimi desteklemeyen diller için tasarlanmıştır.  
  
 Sınıf olarak kullanılan `x:Subclass` iç içe geçmiş bir sınıf olamaz ve `x:Subclass` "Bağımlılıkları" bölümünde açıklandığı gibi kök nesneye başvurması gerekir.  
  
 Aksi takdirde, kavramsal anlamını `x:Subclass` .NET Framework XAML hizmetlerinde uygulama tarafından tanımlı değil. .NET Framework XAML hizmetlerinde davranış tarafından hangi XAML işaretleme ve kod yedekleme bağlı genel programlama modeli belirtmiyor olmasıdır. Daha fazla kavramları uygulamaları ilgili `x:Class` ve `x:Subclass` XAML biçimlendirme derlenmiş biçimlendirme ve CLR tabanlı gerideki bağlanma tanımlamak için programlama modelleri veya uygulama modeli kullandığınız belirli çerçeve tarafından gerçekleştirilir. Her bir çerçeve davranışı ya da yapı ortamına dahil belirli bileşenlerin bazılarını etkinleştirmek, kendi derleme eylemler olabilir. Bir çerçeve içinde yapı eylemleri de arka plan kod için kullanılan belirli bir CLR dil göre değişebilir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `x:Subclass` bir sayfa kök veya <xref:System.Windows.Application> zaten uygulama tanımı kök `x:Class`. Bildirme `x:Subclass` bir sayfası veya uygulama kökü veya yok burada belirtme dışındaki herhangi bir öğede `x:Class` varsa, bir derleme zamanı hatasına neden olur.  
  
 Bu iş için doğru sınıflar türetilmiş oluşturma `x:Subclass` senaryo oldukça karmaşıktır. Ara (dosyaları projenize obj klasöründe bulunan .xaml dosya adlarını dahil edilip derecelendirilir adlarla biçimlendirmesi derleme tarafından üretilen .g) incelemeniz gerekebilir. Bu Ara dosyaları derlenmiş uygulamada birleştirilmiş kısmi sınıflar, belirli programlama yapıları kökenini belirlemenize yardımcı olabilir.  
  
 Türetilmiş sınıf içinde olay işleyicileri olmalıdır `internal override` (`Friend Overrides` Microsoft Visual Basic) saptamalar işleyicileri Ara sınıfı, derleme sırasında oluşturulan geçersiz kılmak için. Aksi takdirde (gölge) Ara sınıf uygulaması türetilen sınıf uygulamaları Gizle ve Ara sınıf işleyicileri çağrılamaz.  
  
 Tanımladığınızda hem `x:Class` ve `x:Subclass`, herhangi bir uygulama tarafından başvurulan sınıfın sağlamak gerekmez `x:Class`. Yalnızca aracılığıyla bir ad vermeniz gerekir `x:Class` derleyici Ara dosyaları (derleyici ı varsayılan adı bu durumda) oluşturan sınıf için bazı yönergeler sahip olacak şekilde özniteliği. Size verebilir `x:Class` uygulama sınıf; ancak, bu her ikisini de kullanarak tipik bir senaryo değildir `x:Class` ve `x:Subclass`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [WPF için XAML ve Özel Sınıflar](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
