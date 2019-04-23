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
ms.openlocfilehash: 9ce0b70bfdd70b47857167ff14e62ed2bbda569d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077465"
---
# <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri
Bu konuda, rehberlik ve özellik türü bir koleksiyon türü olduğu bir bağımlılık özelliği uygulama öğrenmek için önerilen desenler sağlar.  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Koleksiyon türü bağımlılık özelliği uygulama  
 Genel olarak, bir bağımlılık özelliği için tanımladığınız takip ettiğiniz uygulama düzeni olan bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği sarmalayıcı, burada bu özellik destekli bir <xref:System.Windows.DependencyProperty> tanımlayıcısı yerine bir alan veya diğer yapı. Bir koleksiyon türü özelliği uyguladığınızda bu aynı deseni izleyin. Ancak koleksiyonda bulunan tür kendisini olduğunda koleksiyon türü özelliği düzeni karmaşıklık getirir bir <xref:System.Windows.DependencyObject> veya <xref:System.Windows.Freezable> türetilmiş sınıf.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Varsayılan değer dışında koleksiyon başlatılıyor  
 Bağımlılık özelliği oluşturduğunuzda, ilk alan değeri olarak özellik varsayılan değeri belirtmeyin. Bunun yerine, bağımlılık özelliği meta verisi aracılığıyla varsayılan değeri belirtin. Bağımlılık özelliği meta verilerinde belirtilen varsayılan değerin, özellik bir başvuru türü ise, örnek başına varsayılan bir değer değil; Bunun yerine, türün tüm örnekleri için geçerli bir varsayılan değerdir. Bu nedenle yeni oluşturulan örneklerinin çalışan varsayılan değer olarak koleksiyon özelliği meta verileri tarafından tanımlanan tekil statik koleksiyon kullanmayı dikkatli olmanız gerekir. Bunun yerine, kasıtlı olarak koleksiyon değeri benzersiz (örnek) koleksiyonuna sınıfı Oluşturucu mantığınızın bir parçası olarak ayarladığınız emin olmanız gerekir. Aksi takdirde, yanlışlıkla singleton sınıfı oluşturmuş olacaksınız.  
  
 Aşağıdaki örnek göz önünde bulundurun. Aşağıdaki bölümde örneğin bir sınıf tanımını gösterir `Aquarium`. Sınıfı koleksiyon türü bağımlılık özelliğini tanımlar `AquariumObjects`, genel kullanan <xref:System.Collections.Generic.List%601> tür bir <xref:System.Windows.FrameworkElement> tür kısıtlaması. İçinde <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> çağrısı bağımlılık özelliği meta verileri için yeni bir genel varsayılan değer kurar <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Ancak, kod gösterildiği çıktığınız ise, tüm örnekleri için tek bir liste varsayılan değeri paylaşılır `Aquarium`. İki ayrı nasıl ekleneceğini göstermek için tasarlanmıştır aşağıdaki test kodu çalıştırdıysanız `Aquarium` örnekler ve farklı tek `Fish` her biri için şaşırtıcı bir sonuç görmeniz:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Bir sayısına sahip her bir koleksiyon yerine, her bir koleksiyon iki sayısını var! Bunun nedeni, her `Aquarium` eklenen kendi `Fish` varsayılan değer koleksiyonu için bir tek oluşturucu çağrısı meta verilerinde kullanmasından ve bu nedenle tüm örnekleri arasında paylaşılır. Bu neredeyse hiçbir zaman, istediğiniz durumdur.  
  
 Bu sorunu düzeltmek için sınıf oluşturucu çağrısının parçası olarak benzersiz bir örnek için koleksiyon bağımlılık özelliği değeri sıfırlamanız gerekir. Özellik salt okunur bağımlılık özelliği olduğundan, kullandığınız <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> yöntemi kullanarak ayarlamak için <xref:System.Windows.DependencyPropertyKey> olan yalnızca sınıfın içinden erişilebilir.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Şimdi beklenen sonuçları görmeniz aynı kodu yeniden test çalıştırdıysanız, burada her `Aquarium` kendi benzersiz koleksiyonu desteklenmez.  
  
 Okuma-yazma, koleksiyon özelliği seçtiyseniz, bu düzen küçük bir değişim olacaktır. Bu durumda hala anahtarı olmayan imzası çağırma başlatmanın oluşturucudan genel set erişimcisine çağırabilir <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> küme kapsayıcısı içinde bir ortak kullanarak <xref:System.Windows.DependencyProperty> tanımlayıcısı.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Koleksiyon Özellikleri bağlama değeri değişiklikleri raporlama  
 Kendisini bir bağımlılık özelliği olan bir koleksiyon özelliği için onun alt değişiklikleri otomatik olarak bildirmez. Derlemeye bağlamalar oluşturuyorsanız, bu nedenle bazı veri bağlama senaryoları geçersiz kılmalarını değişiklikleri bağlama engelleyebilir. Ancak, koleksiyon türü kullanıyorsanız <xref:System.Windows.FreezableCollection%601> , koleksiyon türü olarak ardından alt özellik değişiklikleri koleksiyondaki içerilen öğelerin düzgün şekilde bildirilir ve bağlama beklendiği gibi çalışır.  
  
 Alt özellik bağlamasını bağımlılık nesne koleksiyonundaki etkinleştirmek için koleksiyon özelliği türü olarak oluşturma <xref:System.Windows.FreezableCollection%601>, o koleksiyon herhangi bir tür kısıtlaması ile <xref:System.Windows.DependencyObject> türetilmiş sınıf.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FreezableCollection%601>
- [WPF için XAML ve Özel Sınıflar](xaml-and-custom-classes-for-wpf.md)
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
