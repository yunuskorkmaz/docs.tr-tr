---
title: Bağlantı olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139846"
---
# <a name="connection-events"></a>Bağlantı olayları
Tüm .NET Framework veri sağlayıcıları **bağlantı** belirlemek için ya da bir veri kaynağından bilgi iletilerini almak için kullanabileceğiniz iki olay nesneleri durumunu bir **bağlantı** sahip değiştirildi. Aşağıdaki tabloda olaylarını açıklar **bağlantı** nesne.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|**InfoMessage**|Bir veri kaynağından bir bilgi iletisidir döndürüldüğünde gerçekleşir. Bilgi iletilerini bir veri kaynağından oluşturulan bir özel durum neden iletileri ' dir.|  
|**StateChange**|Gerçekleşir, durumunu **bağlantı** değişiklikler.|  
  
## <a name="working-with-the-infomessage-event"></a>InfoMessage olayı ile çalışma  
 Bir SQL Server veri kullanarak kaynak uyarıları ve bilgilendirici iletileri alabilirsiniz <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayı <xref:System.Data.SqlClient.SqlConnection> nesne. 16 11 önem derecesi ile veri kaynağından döndürülen hata, bir özel durum oluşturulmasına neden. Ancak, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay, bir hata ile ilişkili olmayan bir veri kaynağından alınan iletileri almak için kullanılabilir. Microsoft SQL Server, söz konusu olduğunda herhangi bir hata önem derecesi 10 veya daha küçük bir bilgi iletisidir olduğu kabul edilir ve kullanılarak yakalanabilir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay. Daha fazla bilgi için [veritabanı altyapısı hata önem dereceleri](/sql/relational-databases/errors-events/database-engine-error-severities) makalesi.
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay aldığında bir <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> nesnesini içeren, içinde kendi **hataları** özelliği, veri kaynağından alınan iletileri koleksiyonu. Sorgulayabilirsiniz **hata** hatanın kaynağının yanı sıra hata sayısı ve ileti metni, bu koleksiyondaki nesneleri. SQL Server için .NET Framework veri sağlayıcısı ayrıca veritabanı, saklı yordam ve iletinin geldiği satır numarası hakkında ayrıntılı bilgi içerir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için bir olay işleyicisi eklemek gösterilmektedir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>InfoMessages hataları işleme  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay normalde sunucudan gönderilen bilgilendirme ve uyarı iletileri için harekete. Ancak, gerçek bir hata oluştuğunda, yürütme **ExecuteNonQuery** veya **ExecuteReader** sunucu işlemi başlatan bir yöntemi durdurulamaz ve bir özel durum oluşturulur.  
  
 Devam etmek istiyorsanız hataları bağımsız olarak bir komut deyimlerin geri kalanını işlem sunucu tarafından üretilen, Ayarla <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> için `true`. Bunun yapılması bağlantı ateşlenmesine neden olur <xref:System.Data.SqlClient.SqlConnection.InfoMessage> yerine bir özel durum ve işleme kesintiye hataları için olay. İstemci uygulaması daha sonra bu olayı işleyin ve hata koşullarını yanıt.  
  
> [!NOTE]
>  Sunucunun komut işlenmeden durdurmak neden bir hata 17 veya üzeri önem düzeyine sahip bir özel durum işlenmesi gerekir. Bu durumda, nasıl hata olarak işlenir bağımsız olarak durum <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.  
  
## <a name="working-with-the-statechange-event"></a>StateChange olayı ile çalışma  
 **StateChange** bir olay oluşursa, durumu bir **bağlantı** değişiklikler. **StateChange** olay aldığında <xref:System.Data.StateChangeEventArgs> durumundaki değişikliği belirlemenize olanak sağlayan **bağlantı** kullanarak **OriginalState** ve **CurrentState** özellikleri. **OriginalState** özelliği bir <xref:System.Data.ConnectionState> durumunu gösteren numaralandırma **bağlantı** önceki değiştirildi. **CurrentState** olduğu bir <xref:System.Data.ConnectionState> durumunu gösteren numaralandırma **bağlantı** değiştirmeden sonra.  
  
 Aşağıdaki kod örneğinde **StateChange** konsola ileti yazmak için olay olduğunda durumu **bağlantı** değişiklikler.  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
