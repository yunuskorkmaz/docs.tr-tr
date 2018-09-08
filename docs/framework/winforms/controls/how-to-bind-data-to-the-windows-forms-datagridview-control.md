---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 4064ef26ee550c02ac8825ac4c1a417472b64de6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138727"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama
<xref:System.Windows.Forms.DataGridView> Denetimi, bir çeşitli veri kaynaklarına bağlanır, böylece standart Windows Forms veri bağlama modelini destekler. Çoğu durumda, ancak siz bağlanacağı bir <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşim ayrıntılarını yönetecek bileşeni. <xref:System.Windows.Forms.BindingSource> Bileşen herhangi bir Windows Forms veri kaynağını temsil edebilir ve seçerek ya da değiştirirken, verilerin konumu büyük esneklik sağlar. Tarafından desteklenen veri kaynakları hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
 Visual Studio'da bu görevi için kapsamlı desteği yoktur.  Ayrıca bkz: [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı için veri bağlama](https://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a>DataGridView denetimi verilere bağlanmak için  
  
1.  Bir veritabanından veri alma ayrıntılarını işlemek için bir yöntem uygulayın. Aşağıdaki kod örneğinde uygular bir `GetData` başlatan yöntem bir <xref:System.Data.SqlClient.SqlDataAdapter> bileşeni ve doldurmak için kullandığı bir <xref:System.Data.DataTable>. <xref:System.Data.DataTable> Sonra bağlı <xref:System.Windows.Forms.BindingSource> bileşeni. Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer. Yüklü SQL Server Northwind örnek veritabanıyla bir sunucuya erişim gerekir.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  Formun içinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi, bağlama <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource> bileşen ve çağrıya `GetData` veritabanından veri almak için yöntemi.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tam örneği veritabanından verilerin yeniden yüklenmesini ve veritabanına değişiklikleri gönderme için düğmeler sağlar.  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Windows.Forms, System.Data ve System.XML derlemesine ilişkin başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
