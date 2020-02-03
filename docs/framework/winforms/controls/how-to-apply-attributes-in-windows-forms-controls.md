---
title: Denetimlere öznitelik uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: b8ecd516cf6bb189c6ad1b208dd8e3a5444f001c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741486"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama
Tasarım ortamıyla doğru şekilde etkileşim kuran ve çalışma zamanında doğru şekilde yürütülen bileşenleri ve denetimleri geliştirmek için, öznitelikleri sınıflara ve üyelere doğru bir şekilde uygulamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir özel denetimde çeşitli özniteliklerin nasıl kullanılacağını göstermektedir. Denetim, basit bir günlüğe kaydetme özelliğini gösterir. Denetim bir veri kaynağına bağlandığında, veri kaynağı tarafından gönderilen değerleri bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntüler. Bir değer `Threshold` özelliği tarafından belirtilen değeri aşarsa `ThresholdExceeded` bir olay tetiklenir.  
  
 `AttributesDemoControl`, değerleri bir `LogEntry` sınıfıyla günlüğe kaydeder. `LogEntry` sınıfı bir şablon sınıfıdır ve bu, günlüğe kaydettiği tür üzerinde parametreleştirilenir. Örneğin, `AttributesDemoControl` `float`türündeki günlüğe kayıt alıyorsa, her `LogEntry` örnek aşağıdaki şekilde tanımlanır ve kullanılır.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> `LogEntry` rastgele bir tür tarafından parametrelendirildiği için, parametre türü üzerinde çalışmak üzere yansıma kullanması gerekir. Eşik özelliğinin çalışması için `T` parametre türü <xref:System.IComparable> arabirimini uygulamalıdır.  
  
 `AttributesDemoControl` barındıran form, düzenli aralıklarla bir performans sayacını sorgular. Her değer uygun türdeki bir `LogEntry` paketlenir ve formun <xref:System.Windows.Forms.BindingSource>eklenir. `AttributesDemoControl`, değeri veri bağlama aracılığıyla alır ve değeri bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntüler.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 İlk kod örneği `AttributesDemoControl` uygulamasıdır. İkinci kod örneği, `AttributesDemoControl`kullanan bir formu gösterir.  
  
## <a name="class-level-attributes"></a>Sınıf düzeyi öznitelikleri  
 Bazı öznitelikler sınıf düzeyinde uygulanır. Aşağıdaki kod örneği, bir Windows Forms denetimine yaygın olarak uygulanan öznitelikleri gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter özniteliği  
 <xref:System.ComponentModel.TypeConverterAttribute>, yaygın olarak kullanılan bir sınıf düzeyi özniteliğidir. Aşağıdaki kod örneği, `LogEntry` sınıfı için kullanımını gösterir. Bu örnek ayrıca `LogEntryTypeConverter`olarak adlandırılan `LogEntry` türü için <xref:System.ComponentModel.TypeConverter> bir uygulamasını gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Üye düzeyi öznitelikleri  
 Bazı öznitelikler üye düzeyinde uygulanır. Aşağıdaki kod örnekleri, Windows Forms denetimlerinin özelliklerine yaygın olarak uygulanan bazı öznitelikleri gösterir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue özniteliği  
 Aşağıdaki örnek, <xref:System.ComponentModel.AmbientValueAttribute> gösterir ve tasarım ortamıyla etkileşimini destekleyen kodu gösterir. Bu etkileşime *Ambience*adı verilir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Veri bağlama öznitelikleri  
 Aşağıdaki örneklerde karmaşık veri bağlamasının bir uygulama gösterilmektedir. Daha önce gösterilen sınıf düzeyi <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, veri bağlama için kullanılacak `DataSource` ve `DataMember` özelliklerini belirtir. <xref:System.ComponentModel.AttributeProviderAttribute>, `DataSource` özelliğinin bağlanacağı türü belirtir.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- `AttributesDemoControl` barındıran form, derlemek için `AttributesDemoControl` derlemesine bir başvuru gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Windows Forms Denetimlerindeki Öznitelikler](attributes-in-windows-forms-controls.md)
- [Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
