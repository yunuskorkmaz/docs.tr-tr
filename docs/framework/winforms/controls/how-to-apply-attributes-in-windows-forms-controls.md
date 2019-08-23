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
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922792"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama
Tasarım ortamıyla doğru şekilde etkileşim kuran ve çalışma zamanında doğru şekilde yürütülen bileşenleri ve denetimleri geliştirmek için, öznitelikleri sınıflara ve üyelere doğru bir şekilde uygulamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir özel denetimde çeşitli özniteliklerin nasıl kullanılacağını göstermektedir. Denetim, basit bir günlüğe kaydetme özelliğini gösterir. Denetim bir veri kaynağına bağlandığında, veri kaynağı tarafından bir <xref:System.Windows.Forms.DataGridView> denetimde gönderilen değerleri görüntüler. Bir değer, `Threshold` özelliği tarafından belirtilen değeri aşarsa bir `ThresholdExceeded` olay tetiklenir.  
  
 Değerleri bir`LogEntry` sınıfıyla günlüğe kaydedilir. `AttributesDemoControl` `LogEntry` Sınıfı, bir şablon sınıfıdır, bu, günlüğe kaydettiği tür üzerinde parametreleştirimiş olması anlamına gelir. Örneğin, Eğer `AttributesDemoControl` , türü `float`günlüğe kaydetme ise, her `LogEntry` örnek aşağıdaki şekilde bildirilmiştir ve kullanılır.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> `LogEntry` , Rastgele bir tür tarafından parametrelendirildiği için, parametre türü üzerinde çalışması için yansıma kullanması gerekir. Eşik özelliğinin çalışması için, parametre türünün `T` <xref:System.IComparable> arabirimini uygulaması gerekir.  
  
 Bir performans sayacını düzenli aralıklarla `AttributesDemoControl` sorgulayan form. Her bir değer uygun bir `LogEntry` tür içinde paketlenmiştir ve <xref:System.Windows.Forms.BindingSource>formun öğesine eklenir. , `AttributesDemoControl` Değeri veri bağlama aracılığıyla alır ve bir <xref:System.Windows.Forms.DataGridView> denetimdeki değeri görüntüler.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 İlk kod örneği `AttributesDemoControl` uygulama. İkinci kod örneği, `AttributesDemoControl`kullanan bir formu gösterir.  
  
## <a name="class-level-attributes"></a>Sınıf düzeyi öznitelikleri  
 Bazı öznitelikler sınıf düzeyinde uygulanır. Aşağıdaki kod örneği, bir Windows Forms denetimine yaygın olarak uygulanan öznitelikleri gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter özniteliği  
 <xref:System.ComponentModel.TypeConverterAttribute>, başka bir yaygın kullanılan sınıf düzeyi özniteliğidir. Aşağıdaki kod örneği, `LogEntry` sınıfı için kullanımını gösterir. Bu örnek ayrıca, olarak adlandırılan <xref:System.ComponentModel.TypeConverter> `LogEntry` `LogEntryTypeConverter`türü için bir uygulamasını gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Üye düzeyi öznitelikleri  
 Bazı öznitelikler üye düzeyinde uygulanır. Aşağıdaki kod örnekleri, Windows Forms denetimlerinin özelliklerine yaygın olarak uygulanan bazı öznitelikleri gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue özniteliği  
 Aşağıdaki örnek öğesini gösterir <xref:System.ComponentModel.AmbientValueAttribute> ve tasarım ortamıyla etkileşimini destekleyen kodu gösterir. Bu etkileşime *Ambience*adı verilir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Veri bağlama öznitelikleri  
 Aşağıdaki örneklerde karmaşık veri bağlamasının bir uygulama gösterilmektedir. Daha önce gösterilen sınıf <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>düzeyi, veri bağlama için kullanılacak `DataSource` ve `DataMember` özelliklerini belirtir. , <xref:System.ComponentModel.AttributeProviderAttribute> `DataSource` Özelliğin bağlanacağı türü belirtir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Öğesini barındıran `AttributesDemoControl` form, derlemek için `AttributesDemoControl` derlemeye bir başvuru gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Windows Forms Denetimlerindeki Öznitelikler](attributes-in-windows-forms-controls.md)
- [Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
