---
title: Bağlantı Olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: a7ad0d4d950da71db0aebca872949fa82669c5c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151708"
---
# <a name="connection-events"></a>Bağlantı Olayları
.NET Framework veri sağlayıcılarının tümünün, bir veri kaynağından bilgi iletileri almak veya **Bağlantının** durumunun değişip değişmediğini belirlemek için kullanabileceğiniz iki olayla **bağlantı** nesneleri vardır. Aşağıdaki tabloda **Bağlantı** nesnesinin olayları açıklanmaktadır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|**ınfomessage**|Bir bilgi iletisi bir veri kaynağından döndürüldüğünde oluşur. Bilgilendirme iletileri, bir özel durum atılmasına neden olmayan bir veri kaynağından gelen iletilerdir.|  
|**Statechange**|**Bağlantının** durumu değiştiğinde oluşur.|  
  
## <a name="working-with-the-infomessage-event"></a>InfoMessage Etkinliği ile çalışma  
 <xref:System.Data.SqlClient.SqlConnection> Nesnenin <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayını kullanarak bir SQL Server veri kaynağından uyarı ve bilgilendirme iletileri alabilirsiniz. Önem düzeyi 11 ile 16 arasında olan veri kaynağından döndürülen hatalar, özel bir durumun atılmasına neden olur. Ancak, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay bir hata ile ilişkili olmayan veri kaynağından iletileri elde etmek için kullanılabilir. Microsoft SQL Server durumunda, şiddeti 10 veya daha az olan herhangi bir hata bilgilendirme iletisi olarak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> kabul edilir ve olay kullanılarak yakalanabilir. Daha fazla bilgi için [Veritabanı Altyapısı Hata Önemleri](/sql/relational-databases/errors-events/database-engine-error-severities) makalesine bakın.
  
 Olay, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> **Hatalar** özelliğinde veri kaynağından gelen iletilerin bir koleksiyonunu içeren bir nesne alır. Hata numarası ve ileti metninin yanı sıra hata nın kaynağı için bu koleksiyondaki **Hata** nesnelerini sorgulayabilirsiniz. SQL Server için .NET Framework Data Provider, iletinin geldiği veritabanı, depolanan yordam ve satır numarası hakkında ayrıntılı bilgi de içerir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, olay için bir olay <xref:System.Data.SqlClient.SqlConnection.InfoMessage> işleyicisinin nasıl ekleyeceğini gösterir.  
  
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
  
## <a name="handling-errors-as-infomessages"></a>Hataları InfoMessage olarak işleme  
 Olay <xref:System.Data.SqlClient.SqlConnection.InfoMessage> normalde yalnızca sunucudan gönderilen bilgilendirme ve uyarı iletileri için ateşlenir. Ancak, gerçek bir hata oluştuğunda, sunucu işlemini başlatan **ExecuteNonQuery** veya **ExecuteReader** yönteminin yürütülmesi durdurulur ve bir özel durum atılır.  
  
 Sunucu tarafından üretilen hatalardan bağımsız olarak ifadelerin geri kalanını bir komutla işlemeye <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> devam <xref:System.Data.SqlClient.SqlConnection> etmek `true`istiyorsanız, 'nin özelliğini . Bunu yapmak, bağlantının <xref:System.Data.SqlClient.SqlConnection.InfoMessage> özel durum atmak ve işleme kesintiye uğratmak yerine olayı hatalardan dolayı ateşlemesine neden olur. İstemci uygulaması daha sonra bu olayı işleyebilir ve hata koşullarına yanıt verebilir.  
  
> [!NOTE]
> Sunucunun komutişlemeyi durdurmasına neden olan 17 veya üzeri önem düzeyine sahip bir hata nın bir özel durum olarak ele alınması gerekir. Bu durumda, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> hatanın olaydaki nasıl işlendiğine bakılmaksızın bir özel durum atılır.  
  
## <a name="working-with-the-statechange-event"></a>StateChange Etkinliği ile Çalışma  
 **StateChange** olayı, **Bağlantının** durumu değiştiğinde oluşur. **OriginalState** ve <xref:System.Data.StateChangeEventArgs> **CurrentState** özelliklerini kullanarak **Bağlantı** nın durumundaki değişikliği belirlemenizi sağlayan **StateChange** olayı alır. **OriginalState** özelliği, <xref:System.Data.ConnectionState> **bağlantının** değişmeden önceki durumunu gösteren bir numaralandırmadır. **CurrentState,** <xref:System.Data.ConnectionState> **bağlantının** değiştirildikten sonraki durumunu gösteren bir numaralandırmadır.  
  
 Aşağıdaki kod örneği, **Bağlantı'nın** durumu değiştiğinde konsola ileti yazmak için **StateChange** olayını kullanır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
