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
ms.openlocfilehash: 1ab54b0c6828a0648fecfc293b6a7143b012ad6a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192177"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama
Bileşen ve Denetim doğru tasarım ortamı ile etkileşimli ve düzgün çalışma zamanında yürüten geliştirmek için öznitelikleri doğru sınıflar ve üyeler uygulama gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, çeşitli öznitelikler özel bir denetimi kullanma gösterilmektedir. Denetim, bir basit günlüğe kaydetme özelliğini gösterir. Denetim bir veri kaynağına bağlandığında, veri kaynağında tarafından gönderilen değerlerini görüntüler. bir <xref:System.Windows.Forms.DataGridView> denetimi. Bir değeri tarafından belirtilen değeri aşarsa `Threshold` özelliği, bir `ThresholdExceeded` olayı oluşturulur.  
  
 `AttributesDemoControl` Değerlerle günlükleri bir `LogEntry` sınıfı. `LogEntry` , Bu günlükleri türüne parametreli anlamına gelir. bir şablon sınıfı. Örneğin, varsa `AttributesDemoControl` günlük değerler türü `float`, her `LogEntry` örneği bildirildi ve şu şekilde kullanılır.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Çünkü `LogEntry` parametrelenmiş bir rastgele türüne göre bu yansıma parametre türü üzerinde çalışılacak kullanmanız gerekir. Eşik özelliğin çalışması, parametre türü `T` uygulamalıdır <xref:System.IComparable> arabirimi.  
  
 Barındıran formun `AttributesDemoControl` bir performans sayacı düzenli aralıklarla sorgular. Her değer, paketlenmiş bir `LogEntry` uygun türde ve formun eklenen <xref:System.Windows.Forms.BindingSource>. `AttributesDemoControl` Değeri kendi veri bağlama aracılığıyla alır ve değerini görüntüler bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 İlk kod örnektir `AttributesDemoControl` uygulaması. İkinci kod örneğinde kullanan bir form gösterir `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Sınıf düzeyinde öznitelikler  
 Bazı öznitelikler sınıf düzeyinde uygulanır. Aşağıdaki kod örneği, bir Windows Forms denetimi için yaygın olarak uygulanan öznitelikleri gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Atribut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute> başka bir yaygın olarak kullanılan sınıf düzeyi özniteliğidir. Aşağıdaki kod örneği, uygunsa kullanımını gösterir `LogEntry` sınıfı. Bu örnek ayrıca uygulanışı gösterilmektedir bir <xref:System.ComponentModel.TypeConverter> için `LogEntry` adlı türü `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Üye düzeyinde öznitelikler  
 Bazı öznitelikler üye düzeyinde uygulanır. Aşağıdaki kod örnekleri Windows Forms denetimlerindeki özellikler için yaygın olarak uygulanan bazı öznitelikler gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue özniteliği  
 Aşağıdaki örnek, gösterir <xref:System.ComponentModel.AmbientValueAttribute> ve tasarım ortamı ile etkileşimi destekleyen ilişkili kodları göstermektedir. Bu etkileşimi adlı *çevre*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Veri bağlama öznitelikleri  
 Aşağıdaki örnekler, karmaşık veri bağlama uygulanışı gösterilmektedir. Sınıf düzeyi <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>gösterilen önceden belirtir `DataSource` ve `DataMember` kullanmak için veri bağlama özellikleri. <xref:System.ComponentModel.AttributeProviderAttribute> Türün belirtir `DataSource` bağlama özellikleri.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Barındıran formun `AttributesDemoControl` başvurusu gerektirir `AttributesDemoControl` oluşturmak için derleme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Windows Forms Denetimlerindeki Öznitelikler](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
