---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c3be381f67ae57e9fbd9dd526d4d3364c864903
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama
<xref:System.Windows.Forms.DataGridView> Denetimi, çeşitli veri kaynakları için bağlı olacağı şekilde standart Windows Forms veri bağlama modelini destekler. Çoğu durumda, ancak siz bağlanacağı bir <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bileşeni. <xref:System.Windows.Forms.BindingSource> Bileşeni herhangi bir Windows Forms veri kaynağını temsil edebilir ve seçme veya değiştirirken, verilerin konumu büyük esneklik sağlar. Tarafından desteklenen veri kaynakları hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
 Visual Studio'da bu görev için kapsamlı destek yoktur.  Ayrıca bkz. [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı veri bağlama](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a>DataGridView denetimine veri bağlanmak için  
  
1.  Bir veritabanından veri alma ayrıntılarını işlemek için koruma yöntemi uygulayabilirsiniz. Aşağıdaki kod örneği uygulayan bir `GetData` başlatır yöntemi bir <xref:System.Data.SqlClient.SqlDataAdapter> bileşen ve doldurmak için kullandığı bir <xref:System.Data.DataTable>. <xref:System.Data.DataTable> Sonra bağlı <xref:System.Windows.Forms.BindingSource> bileşeni. Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer. Northwind SQL Server örnek veritabanı yüklenmiş bir sunucuya erişimi gerekir.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  Formun içinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi, BIND <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource> bileşeni ve çağrı `GetData` veritabanından veri almak için yöntem.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tam kod örnek veritabanındaki verileri yeniden yüklemeyi ve değişiklikleri veritabanına göndermek için düğmeler sağlar.  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Windows.Forms, System.Data ve System.XML derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
