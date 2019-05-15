---
title: 'Nasıl yapılır: BindingSource ve ResetItem Yöntemini Kullanarak Değişiklik Bildirimleri Verme'
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
ms.openlocfilehash: 39beb5c7162fb01a51360330216687c158ff433c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583718"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>Nasıl yapılır: BindingSource ve ResetItem Yöntemini Kullanarak Değişiklik Bildirimleri Verme
Öğeleri değiştirildi, eklendiğinde veya bazı veri kaynakları, denetimler için değişiklik bildirimleri geçirmeyin. İle <xref:System.Windows.Forms.BindingSource> bileşeni gibi veri kaynaklarına bağlamak ve bir değişiklik bildirimi kodunuzdan Yükselt.  
  
## <a name="example"></a>Örnek  
 Bu formu kullanmayı gösterir. bir <xref:System.Windows.Forms.BindingSource> listeye bağlamak için bileşen bir <xref:System.Windows.Forms.DataGridView> denetimi. Listenin değişiklik bildirimleri geçirmemesi böylece <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodunda <xref:System.Windows.Forms.BindingSource> listesindeki bir öğe değiştirildiğinde çağrılır. biçimindeki telefon numarasıdır.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
