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
# <a name="connection-events"></a><span data-ttu-id="b7ec7-102">Bağlantı Olayları</span><span class="sxs-lookup"><span data-stu-id="b7ec7-102">Connection Events</span></span>
<span data-ttu-id="b7ec7-103">.NET Framework veri sağlayıcılarının tümünün, bir veri kaynağından bilgi iletileri almak veya **Bağlantının** durumunun değişip değişmediğini belirlemek için kullanabileceğiniz iki olayla **bağlantı** nesneleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="b7ec7-104">Aşağıdaki tabloda **Bağlantı** nesnesinin olayları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="b7ec7-105">Olay</span><span class="sxs-lookup"><span data-stu-id="b7ec7-105">Event</span></span>|<span data-ttu-id="b7ec7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7ec7-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b7ec7-107">**ınfomessage**</span><span class="sxs-lookup"><span data-stu-id="b7ec7-107">**InfoMessage**</span></span>|<span data-ttu-id="b7ec7-108">Bir bilgi iletisi bir veri kaynağından döndürüldüğünde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="b7ec7-109">Bilgilendirme iletileri, bir özel durum atılmasına neden olmayan bir veri kaynağından gelen iletilerdir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="b7ec7-110">**Statechange**</span><span class="sxs-lookup"><span data-stu-id="b7ec7-110">**StateChange**</span></span>|<span data-ttu-id="b7ec7-111">**Bağlantının** durumu değiştiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="b7ec7-112">InfoMessage Etkinliği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b7ec7-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="b7ec7-113"><xref:System.Data.SqlClient.SqlConnection> Nesnenin <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayını kullanarak bir SQL Server veri kaynağından uyarı ve bilgilendirme iletileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="b7ec7-114">Önem düzeyi 11 ile 16 arasında olan veri kaynağından döndürülen hatalar, özel bir durumun atılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="b7ec7-115">Ancak, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay bir hata ile ilişkili olmayan veri kaynağından iletileri elde etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="b7ec7-116">Microsoft SQL Server durumunda, şiddeti 10 veya daha az olan herhangi bir hata bilgilendirme iletisi olarak <xref:System.Data.SqlClient.SqlConnection.InfoMessage> kabul edilir ve olay kullanılarak yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="b7ec7-117">Daha fazla bilgi için [Veritabanı Altyapısı Hata Önemleri](/sql/relational-databases/errors-events/database-engine-error-severities) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="b7ec7-118">Olay, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> **Hatalar** özelliğinde veri kaynağından gelen iletilerin bir koleksiyonunu içeren bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="b7ec7-119">Hata numarası ve ileti metninin yanı sıra hata nın kaynağı için bu koleksiyondaki **Hata** nesnelerini sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="b7ec7-120">SQL Server için .NET Framework Data Provider, iletinin geldiği veritabanı, depolanan yordam ve satır numarası hakkında ayrıntılı bilgi de içerir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b7ec7-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7ec7-121">Example</span></span>  
 <span data-ttu-id="b7ec7-122">Aşağıdaki kod örneği, olay için bir olay <xref:System.Data.SqlClient.SqlConnection.InfoMessage> işleyicisinin nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="b7ec7-123">Hataları InfoMessage olarak işleme</span><span class="sxs-lookup"><span data-stu-id="b7ec7-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="b7ec7-124">Olay <xref:System.Data.SqlClient.SqlConnection.InfoMessage> normalde yalnızca sunucudan gönderilen bilgilendirme ve uyarı iletileri için ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="b7ec7-125">Ancak, gerçek bir hata oluştuğunda, sunucu işlemini başlatan **ExecuteNonQuery** veya **ExecuteReader** yönteminin yürütülmesi durdurulur ve bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="b7ec7-126">Sunucu tarafından üretilen hatalardan bağımsız olarak ifadelerin geri kalanını bir komutla işlemeye <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> devam <xref:System.Data.SqlClient.SqlConnection> etmek `true`istiyorsanız, 'nin özelliğini .</span><span class="sxs-lookup"><span data-stu-id="b7ec7-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="b7ec7-127">Bunu yapmak, bağlantının <xref:System.Data.SqlClient.SqlConnection.InfoMessage> özel durum atmak ve işleme kesintiye uğratmak yerine olayı hatalardan dolayı ateşlemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="b7ec7-128">İstemci uygulaması daha sonra bu olayı işleyebilir ve hata koşullarına yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7ec7-129">Sunucunun komutişlemeyi durdurmasına neden olan 17 veya üzeri önem düzeyine sahip bir hata nın bir özel durum olarak ele alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="b7ec7-130">Bu durumda, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> hatanın olaydaki nasıl işlendiğine bakılmaksızın bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="b7ec7-131">StateChange Etkinliği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="b7ec7-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="b7ec7-132">**StateChange** olayı, **Bağlantının** durumu değiştiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="b7ec7-133">**OriginalState** ve <xref:System.Data.StateChangeEventArgs> **CurrentState** özelliklerini kullanarak **Bağlantı** nın durumundaki değişikliği belirlemenizi sağlayan **StateChange** olayı alır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="b7ec7-134">**OriginalState** özelliği, <xref:System.Data.ConnectionState> **bağlantının** değişmeden önceki durumunu gösteren bir numaralandırmadır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="b7ec7-135">**CurrentState,** <xref:System.Data.ConnectionState> **bağlantının** değiştirildikten sonraki durumunu gösteren bir numaralandırmadır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="b7ec7-136">Aşağıdaki kod örneği, **Bağlantı'nın** durumu değiştiğinde konsola ileti yazmak için **StateChange** olayını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7ec7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-137">See also</span></span>

- [<span data-ttu-id="b7ec7-138">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="b7ec7-138">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="b7ec7-139">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b7ec7-139">ADO.NET Overview</span></span>](ado-net-overview.md)
