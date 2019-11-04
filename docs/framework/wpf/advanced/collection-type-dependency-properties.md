---
title: Koleksiyon Türü Bağımlılık Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: f7f8c25844f41dd8915c0f4404d6714b4c81233c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458466"
---
# <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri
Bu konu, özelliğin türünün bir koleksiyon türü olduğu bir bağımlılık özelliğinin nasıl uygulanacağı hakkında rehberlik ve önerilen desenler sağlar.  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Koleksiyon türü bağımlılık özelliği uygulama  
 Genel olarak bir bağımlılık özelliği için, takip ettiğiniz uygulama deseninin, bu özelliğin bir alan veya diğer yapı yerine bir <xref:System.Windows.DependencyProperty> tanımlayıcı tarafından desteklendiği bir CLR özellik sarmalayıcısı tanımlamanız gerekir. Koleksiyon türü özelliğini uygularken bu aynı kalıbı takip edersiniz. Ancak, bir koleksiyon türü özelliği, koleksiyonda bulunan tür her bir <xref:System.Windows.DependencyObject> veya <xref:System.Windows.Freezable> türetilmiş sınıf olduğunda, düzene yönelik bazı karmaşıklıklar getirir.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Koleksiyon varsayılan değerin ötesinde başlatılıyor  
 Bir bağımlılık özelliği oluşturduğunuzda, özelliğin varsayılan değerini başlangıç alanı değeri olarak belirtmeyin. Bunun yerine, bağımlılık özelliği meta verileri aracılığıyla varsayılan değeri belirtirsiniz. Eğer özelliği bir başvuru türü ise, bağımlılık özelliği meta verilerinde belirtilen varsayılan değer örnek başına varsayılan değer değildir; Bunun yerine, türün tüm örnekleri için geçerli olan varsayılan bir değerdir. Bu nedenle, bir koleksiyon özelliği meta verileri tarafından tanımlanan tekil statik koleksiyonu, yeni oluşturulan örnekler için çalışma varsayılan değeri olarak kullanmamaya dikkat etmeniz gerekir. Bunun yerine, koleksiyon değerini sınıf Oluşturucu mantığınızın bir parçası olarak benzersiz bir (örnek) koleksiyona ayarladığınızdan emin olmanız gerekir. Aksi takdirde, istemeden tek bir sınıf oluşturmuş olursunuz.  
  
 Aşağıdaki örneği göz önünde bulundurun. Örneğin aşağıdaki bölümünde bir sınıf `Aquarium`tanımı gösterilmektedir. Sınıfı, bir <xref:System.Windows.FrameworkElement> tür kısıtlaması ile genel <xref:System.Collections.Generic.List%601> türünü kullanan `AquariumObjects`koleksiyon türü bağımlılık özelliğini tanımlar. Bağımlılık özelliği için <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> çağrısında, meta veriler varsayılan değeri yeni bir genel <xref:System.Collections.Generic.List%601>olarak belirler.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Ancak, yalnızca kodu gösterildiği gibi bıraktıysanız, bu tek liste varsayılan değeri tüm `Aquarium`örnekleri için paylaşılır. İki ayrı `Aquarium` örneğinin örneğini nasıl örneklendiribileceğinizi ve bunların her birine tek bir farklı `Fish` nasıl ekleneceğini göstermek için tasarlanan aşağıdaki test kodunu çalıştırdıysanız, ortaya çıkmış bir sonuç görürsünüz:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Her koleksiyonun bir sayısına sahip olması yerine, her koleksiyonun iki sayısı vardır! Bunun nedeni, her bir `Aquarium` Meta verilerdeki tek bir Oluşturucu çağrısından kaynaklanan ve bu nedenle tüm örnekler arasında paylaşıldığı varsayılan değer koleksiyonuna `Fish` ekledik. Bu durum neredeyse hiçbir şekilde istediğiniz şeydir.  
  
 Bu sorunu düzeltmek için, koleksiyon bağımlılığı özellik değerini, sınıf Oluşturucu çağrısının bir parçası olarak benzersiz bir örneğe sıfırlamanız gerekir. Özelliği salt okunurdur bir bağımlılık özelliği olduğundan, yalnızca sınıfı içinde erişilebilir olan <xref:System.Windows.DependencyPropertyKey> kullanarak onu ayarlamak için <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> yöntemini kullanırsınız.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Artık aynı test kodunu yeniden çalıştırdıysanız, her `Aquarium` kendi benzersiz koleksiyonunu desteklediği beklenen sonuçları görebilirsiniz.  
  
 Koleksiyon özelliğinin okuma-yazma olmasını seçtiyseniz bu düzende küçük bir değişim olur. Bu durumda, başlatma yapmak için oluşturucudan ortak küme erişimcisini çağırabilirsiniz. Bu, genel bir <xref:System.Windows.DependencyProperty> tanımlayıcısı kullanarak, küme sarmalayıcı içinde <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> anahtar olmayan imzayı çağırmaya devam eder.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Koleksiyon özelliklerindeki değer değişikliklerini raporlama  
 Kendisi bir bağımlılık özelliği olan bir koleksiyon özelliği, alt özelliklerine yapılan değişiklikleri otomatik olarak raporlamaz. Bir koleksiyona bağlamalar oluşturuyorsanız, bu, bağlamanın değişiklikleri raporlamasına engel olabilir ve bu nedenle bazı veri bağlama senaryolarını geçersiz hale getirebilirsiniz. Ancak, koleksiyon türü <xref:System.Windows.FreezableCollection%601> koleksiyon türü olarak kullanırsanız, koleksiyonda içerilen öğelerin alt özellik değişiklikleri doğru şekilde raporlanır ve bağlama beklendiği gibi çalışacaktır.  
  
 Bağımlılık nesne koleksiyonunda alt özellik bağlamasını etkinleştirmek için, koleksiyon özelliğini <xref:System.Windows.FreezableCollection%601>türü olarak oluşturun ve bu koleksiyonun herhangi bir <xref:System.Windows.DependencyObject> türetilmiş sınıfa bir tür kısıtlaması vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FreezableCollection%601>
- [WPF için XAML ve Özel Sınıflar](xaml-and-custom-classes-for-wpf.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
