---
title: 'Nasıl yapılır: İletişim kutusunu açın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 0ed41d212eee74d0c3eed1d3341d64a6abc876a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638151"
---
# <a name="how-to-open-a-dialog-box"></a>Nasıl yapılır: İletişim kutusunu açın
Bu örnek, bir iletişim kutusunu açmak gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir iletişim kutusu örneği tarafından açılan bir penceredir <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.ShowDialog%2A> yöntemi. <xref:System.Windows.Window.ShowDialog%2A> bir pencere açılır ve yeni iletişim kutusu kapatıldı kadar döndürmüyor. Bu pencere türü olarak da bilinen olduğu bir *kalıcı* penceresinde ve kullanıcı girişini kısıtlayan.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağırma <xref:System.Windows.Window.ShowDialog%2A> tüm windows ve kısıtlama olmaksızın kullanıcı girdi olaylarını kullanma izni gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İletişim Kutusu Sonucu Döndürme](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
