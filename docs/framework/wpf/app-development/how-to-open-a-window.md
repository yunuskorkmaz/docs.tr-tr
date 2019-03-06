---
title: 'Nasıl yapılır: Bir pencere aç'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373575"
---
# <a name="how-to-open-a-window"></a>Nasıl yapılır: Bir pencere aç
Bu örnek, bir pencere aç gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Örnekleme tarafından bir pencere açılırsa <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.Show%2A> yöntemi. <xref:System.Windows.Window.Show%2A> bir pencere açılır ve yeni penceresini kapatmak beklenmeden hemen döndürür. Bu pencere türü de denir bir *geçici* penceresinde ve kullanıcı girişi kısıtlamaz.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Örnekleme <xref:System.Windows.Window> güvenli olmayan yerel yöntemleri çağırma izni gerektirir (bkz <xref:System.Windows.Window.%23ctor%2A>).
