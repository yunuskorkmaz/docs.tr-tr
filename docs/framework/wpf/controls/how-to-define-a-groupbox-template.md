---
title: 'Nasıl yapılır: GroupBox Şablonu Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: a47ce896be4d1c38147584dd80b1bc841737d526
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062513"
---
# <a name="how-to-define-a-groupbox-template"></a>Nasıl yapılır: GroupBox Şablonu Tanımlama
Bu örnek için bir şablonun nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.GroupBox> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Controls.GroupBox> denetim şablonu kullanarak bir <xref:System.Windows.Controls.Grid> denetim düzeni için. Şablonu kullanan bir <xref:System.Windows.Controls.BorderGapMaskConverter> kenarlığını tanımlamak için <xref:System.Windows.Controls.GroupBox> kenarlık getirmeyecek böylece <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> içeriği.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.GroupBox>  
 [GroupBox nasıl yapılır konuları](https://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
