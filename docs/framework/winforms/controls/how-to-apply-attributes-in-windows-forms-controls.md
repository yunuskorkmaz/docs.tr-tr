---
title: 'Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 49c2aaa48a48e33a71b5112db31991975011551d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529642"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama
Bileşenleri ve doğru tasarım ortamı ile etkileşim ve doğru şekilde çalışma zamanında yürütmek denetimleri geliştirmek için sınıflar ve üyeleri öznitelikleri doğru uygulamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, özel bir denetim birkaç öznitelik kullanımı gösterilmiştir. Denetim basit günlük özelliğini gösterir. Denetim bir veri kaynağına bağlandığında, veri kaynağında gönderdiği değerlerini görüntüler bir <xref:System.Windows.Forms.DataGridView> denetim. Bir değer tarafından belirtilen değeri aşarsa `Threshold` özelliği, bir `ThresholdExceeded` olayı oluşturulur.  
  
 `AttributesDemoControl` Değerlerle günlüklerini bir `LogEntry` sınıfı. `LogEntry` , Bu günlükleri türüne parametreli anlamına gelir bir şablon sınıfı bir sınıftır. Örneğin, varsa `AttributesDemoControl` günlük türü değerleri olan `float`, her `LogEntry` örneği bildirilir ve aşağıdaki gibi kullanılır.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Çünkü `LogEntry` parametrelenmiş rasgele bir türe göre onu yansıma parametre türü üzerinde çalışması için kullanmanız gerekir. Eşik özelliğinin çalışması, parametre türü `T` uygulamalıdır <xref:System.IComparable> arabirimi.  
  
 Barındıran form `AttributesDemoControl` bir performans sayacı düzenli aralıklarla sorgular. Her değer paketlenmiştir bir `LogEntry` uygun türde ve formun eklenen <xref:System.Windows.Forms.BindingSource>. `AttributesDemoControl` Değeri, veri bağlama aracılığıyla alır ve değerini görüntüler bir <xref:System.Windows.Forms.DataGridView> denetim.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 İlk bir kod örneğidir `AttributesDemoControl` uygulaması. İkinci kod örneğinde kullanan bir form gösterilmektedir `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Sınıf düzeyi öznitelikleri  
 Bazı öznitelikler sınıf düzeyinde uygulanır. Aşağıdaki kod örneği, bir Windows Forms denetimi için yaygın olarak uygulanan öznitelikleri gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Typeconverter'a özniteliği  
 <xref:System.ComponentModel.TypeConverterAttribute> başka bir yaygın olarak kullanılan sınıf düzeyi özniteliğidir. Aşağıdaki kod örneği, kullanım için gösterir `LogEntry` sınıfı. Bu örnek ayrıca uygulaması gösterir bir <xref:System.ComponentModel.TypeConverter> için `LogEntry` adlı türü `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Üye düzeyi öznitelikleri  
 Bazı öznitelikler üye düzeyinde uygulanır. Aşağıdaki kod örnekleri, yaygın olarak Windows Forms denetimleri özelliklerine uygulanan bazı öznitelikler gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue özniteliği  
 Aşağıdaki örnekte gösterilmiştir <xref:System.ComponentModel.AmbientValueAttribute> ve tasarım ortamı ile etkileşimi destekler kodu gösterir. Bu etkileşimi adlı *çevre*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Veri bağlama öznitelikleri  
 Aşağıdaki örnekler, karmaşık veri bağlama uygulaması göstermektedir. Sınıf düzeyi <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>gösterilen daha önce belirtir `DataSource` ve `DataMember` veri bağlaması için kullanılacak özellikler. <xref:System.ComponentModel.AttributeProviderAttribute> Türün belirtir `DataSource` özelliğini bağlayın.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Barındıran form `AttributesDemoControl` başvuru gerektirir `AttributesDemoControl` oluşturmak için derleme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Windows Forms Denetimlerindeki Öznitelikler](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
