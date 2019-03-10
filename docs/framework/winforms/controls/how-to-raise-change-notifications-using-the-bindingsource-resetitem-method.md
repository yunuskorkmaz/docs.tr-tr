---
title: 'Nasıl yapılır: BindingSource ve Resetıtem metodunu kullanarak değişiklik bildirimleri Yükselt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: a24adf06999784476cd40b91ed53c068b94819e0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721904"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>Nasıl yapılır: BindingSource ve Resetıtem metodunu kullanarak değişiklik bildirimleri Yükselt
Öğeleri değiştirildi, eklendiğinde veya bazı veri kaynakları, denetimler için değişiklik bildirimleri geçirmeyin. İle <xref:System.Windows.Forms.BindingSource> bileşeni gibi veri kaynaklarına bağlamak ve bir değişiklik bildirimi kodunuzdan Yükselt.  
  
## <a name="example"></a>Örnek  
 Bu formu kullanmayı gösterir. bir <xref:System.Windows.Forms.BindingSource> listeye bağlamak için bileşen bir <xref:System.Windows.Forms.DataGridView> denetimi. Listenin değişiklik bildirimleri geçirmemesi böylece <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodunda <xref:System.Windows.Forms.BindingSource> listesindeki bir öğe değiştirildiğinde çağrılır. biçimindeki telefon numarasıdır.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
