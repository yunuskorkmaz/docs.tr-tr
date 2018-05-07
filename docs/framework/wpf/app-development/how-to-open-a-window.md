---
title: 'Nasıl yapılır: bir pencere aç'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 23dc74666d8f47a0fb735d96ad22ed56c96bdbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-a-window"></a>Nasıl yapılır: bir pencere aç
Bu örnek, bir pencere aç gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir pencere oluşturarak açıldığında <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.Show%2A> yöntemi. <xref:System.Windows.Window.Show%2A> bir pencere açılır ve yeni penceresini kapatmak beklenmeden hemen döndürür. Bu pencere olarak da bilinen türünde bir *kalıcı olmayan* penceresinde ve kullanıcı girişini kısıtlamaz.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Örnek oluşturma <xref:System.Windows.Window> güvenli olmayan yerel yöntemleri çağırmak için izin gerektirir (bkz: <xref:System.Windows.Window.%23ctor%2A>).
