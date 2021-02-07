---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel örnek deposu oluşturma'
title: 'Nasıl yapılır: Özel Örnek Deposu Oluşturma'
ms.date: 03/30/2017
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
ms.openlocfilehash: 3a1a511e6a97dffe510c839aceec8c9d91a77ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742140"
---
# <a name="how-to-create-a-custom-instance-store"></a>Nasıl yapılır: Özel Örnek Deposu Oluşturma

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, iş akışı verilerini kalıcı hale getirmek için SQL Server kullanan bir örnek deposu içerir. Uygulamanızın iş akışı verilerinin başka bir ortama (örneğin, farklı bir veritabanı veya dosya sistemi gibi) kalıcı hale getirilmesi gerekiyorsa, özel bir örnek deposu uygulayabilirsiniz. Özel bir örnek deposu, soyut <xref:System.Runtime.DurableInstancing.InstanceStore> sınıfı genişleterek ve uygulama için gerekli yöntemler uygulanmasıyla oluşturulur. Özel bir örnek deposunun tamamen uygulanması için bkz. [Kurumsal satın alma işlemi](./samples/corporate-purchase-process.md) örneği.

## <a name="implementing-the-begintrycommand-method"></a>BeginTryCommand yöntemini uygulama

, <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> Kalıcılık altyapısı tarafından örnek deposuna gönderilir. `command`Parametrenin türü hangi komutun yürütüldüğünü gösterir; Bu parametre aşağıdaki türlerde olabilir:

- <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: Kalıcılık altyapısı, bir iş akışı depolama ortamına kalıcı hale geldiğinde bu komutu örnek deposuna gönderir. İş akışı kalıcılığı verileri, <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> parametresinin üyesinde yöntemine sağlanır `command` .

- <xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: Kalıcılık altyapısı, depolama ortamında bir iş akışı yüklendiğinde bu komutu örnek deposuna gönderir. Yüklenecek iş akışının örnek KIMLIĞI, `instanceId` parametresinin özelliğinin parametresindeki yöntemine sağlanır <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> `context` .

- <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: Kalıcılık altyapısı, bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> kilit sahibi olarak kaydedilmesi gerektiğinde bu komutu örnek deposuna gönderir. Geçerli iş akışının örnek KIMLIĞI, parametresinin yöntemi kullanılarak örnek deposuna sağlanmalıdır <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> `context` .

     Aşağıdaki kod parçacığı, açık bir kilit sahibini atamak için CreateWorkflowOwner komutunun nasıl uygulanacağını gösterir.

    ```csharp
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");
    ...
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()
    {
        InstanceOwnerMetadata =
        {
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },
        }
    };
    InstanceHandle ownerHandle = store.CreateInstanceHandle();
    store.DefaultInstanceOwner = store.Execute(
                                   ownerHandle,
                                   createCommand,
                                   TimeSpan.FromSeconds(30)).InstanceOwner;
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });
    ```

- <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: Bir kilit sahibinin örnek KIMLIĞI örnek deposundan kaldırılabileceği için kalıcılık altyapısı bu komutu örnek deposuna gönderir. İle olduğu gibi <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand> , kilit SAHIBININ kimliği uygulama tarafından sağlanmalıdır.

     Aşağıdaki kod parçacığı kullanarak bir kilidin nasıl yayınlanacağını göstermektedir <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand> .

    ```csharp
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)
    {
        handle.Free();
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);
        try
        {
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.
            Thread.Sleep(10000);
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));
        }
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }
        catch (Exception ex) { Log.Inform(ex.Message); }
        finally
        {
            handle.Free();
            store.DefaultInstanceOwner = null;
        }
    }
    ```

     Bir alt örnek çalıştırıldığında, Yukarıdaki yöntem bir try/catch bloğunda çağrılmalıdır.

    ```csharp
    try
    {
        childInstance.Run();
    }
    catch (Exception)
    {
        throw ;
    }
    finally
    {
        FreeHandleAndDeleteOwner(store, ownerHandle);
    }
    ```

- <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: Kalıcılık altyapısı, bir iş akışı örneği iş akışının örnek anahtarı kullanılarak yüklenecek şekilde bu komutu örnek deposuna gönderir. Örnek anahtarın KIMLIĞI, <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> komutunun parametresi kullanılarak belirlenebilir.

- <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: Kalıcılık altyapısı, iş akışlarını yükleyebilen bir iş akışı konağı oluşturmak için kalıcı iş akışlarının etkinleştirme parametrelerini almak üzere bu komutu örnek deposuna gönderir. Bu komut, <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> etkinleştirilecektir bir örnek bulduktan sonra, öğesini konağa veren örnek deposuna yanıt olarak altyapı tarafından gönderilir. Örnek deposu, etkinleştirilabilecek iş akışlarının olup olmadığını belirlemektir.

- <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: Kalıcılık altyapısı, çalıştırılabilir iş akışı örneklerini yüklemek için bu komutu örnek deposuna gönderir. Bu komut, <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> çalıştırılabilir bir örnek bulduktan sonra, öğesini konağa veren örnek deposuna yanıt olarak altyapı tarafından gönderilir. Örnek deposu çalıştırılabilen iş akışlarını yoklamalıdır. Aşağıdaki kod parçacığı, çalıştırılabilen veya etkinleştirilabilecek iş akışları için bir örnek deposunun yoklanması gerektiğini gösterir.

    ```csharp
    public void PollForEvents()
    {
        InstanceOwner[] storeOwners = this.GetInstanceOwners();

        foreach (InstanceOwner owner in storeOwners)
        {
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))
            {
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))
                {
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivatable);
                    if (hasRunnable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))
                {
                   bool hasActivatable = GetActivatableEvents(this.StoreId, owner.InstanceOwnerId);
                   if (hasActivatable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
            }
        }
    }
    ```

     Yukarıdaki kod parçacığında, örnek deposu kullanılabilir olayları sorgular ve bir olay olup olmadığını anlamak için her birini inceler <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> . Bir tane bulunursa, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> örnek deposuna komut göndermek için ana bilgisayarı bildirmek üzere çağırılır. Aşağıdaki kod parçacığı, bu komut için bir işleyicinin uygulamasını gösterir.

    ```csharp
    If (command is TryLoadRunnableWorkflowCommand)
    {
        Owner owner;
        CheckOwner(context, command.Name, out owner);
        // Checking instance.Owner is like an InstanceLockQueryResult.
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));

        XName ownerService = null;
        InstanceValue value;
        Instance runnableInstance = default(Instance);
        bool foundRunnableInstance = false;

        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);
        if (value != null && value.Value is XName)
        {
            ownerService = (XName)value.Value;
        }

        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)
        {
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)
            {
                continue;
            }

            if (ownerService != null)
            {
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);
                if (value == null || ((XName)value.Value) != ownerService)
                {
                    continue;
                }
            }

            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);
            if (value != null && value.Value != null && value.Value is string)
            {
                continue;
            }

            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")
            {
                runnableInstance = instance.Value;
                foundRunnableInstance = true;
            }

            if (!foundRunnableInstance)
            {
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)
                {
                    runnableInstance = instance.Value;
                    foundRunnableInstance = true;
                }
            }

            if (foundRunnableInstance)
            {
                runnableInstance.LockVersion++;
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;
                MemoryStore.instances[instance.Key] = runnableInstance;
                context.BindInstance(instance.Key);
                context.BindAcquiredLock(runnableInstance.LockVersion);

                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)
                {
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)
                {
                    if (keyEntry.Value.Completed)
                    {
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                    else
                    {
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                }
            }

            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);
            break;
        }
    }
    ```

    Yukarıdaki kod parçacığında örnek deposu, çalıştırılabilir örnekleri arar. Bir örnek bulunursa, yürütme bağlamına bağlanır ve yüklenir.

## <a name="using-a-custom-instance-store"></a>Özel örnek deposu kullanma

Özel bir örnek deposu uygulamak için, örneğine örnek deposunun bir örneğini atayın <xref:System.Activities.WorkflowApplication.InstanceStore%2A> ve <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> yöntemini uygulayın. Ayrıntılar için bkz. [nasıl yapılır: uzun süre çalışan Iş akışı öğreticisi oluşturma ve çalıştırma](how-to-create-and-run-a-long-running-workflow.md) .

## <a name="a-sample-instance-store"></a>Örnek bir örnek deposu

Aşağıdaki kod örneği, [Kurumsal satın alma işlemi](./samples/corporate-purchase-process.md) örneğinden alınan bir bütün örnek depolama uygulamasıdır. Bu örnek depo, iş akışı verilerinin XML kullanarak bir dosyaya devam ettirir.

```csharp
using System;
using System.Activities.DurableInstancing;
using System.Collections.Generic;
using System.IO;
using System.Runtime.DurableInstancing;
using System.Runtime.Serialization;
using System.ServiceModel.Persistence;
using System.Xml;
using System.Xml.Linq;

namespace Microsoft.Samples.WF.PurchaseProcess
{

    public class XmlWorkflowInstanceStore : InstanceStore
    {
        Guid ownerInstanceID;

        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())
        {

        }

        public XmlWorkflowInstanceStore(Guid id)
        {
            ownerInstanceID = id;
        }

        //Synchronous version of the Begin/EndTryCommand functions
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)
        {
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));
        }

        //The persistence engine will send a variety of commands to the configured InstanceStore,
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.
        //This method is where we will handle those commands
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)
        {
            IDictionary<XName, InstanceValue> data = null;

            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle
            if (command is CreateWorkflowOwnerCommand)
            {
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());
            }
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key
            else if (command is SaveWorkflowCommand)
            {
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;
                data = saveCommand.InstanceData;

                Save(data);
            }
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle
            else if (command is LoadWorkflowCommand)
            {
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);

                try
                {
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))
                    {
                        data = LoadInstanceDataFromFile(inputStream);
                        //load the data into the persistence Context
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);
                    }
                }
                catch (Exception exception)
                {
                    throw new PersistenceException(exception.Message);
                }
            }

            return new CompletedAsyncResult<bool>(true, callback, state);
        }

        protected override bool EndTryCommand(IAsyncResult result)
        {
            return CompletedAsyncResult<bool>.End(result);
        }

        //Reads data from xml file and creates a dictionary based off of that.
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)
        {
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();

            NetDataContractSerializer s = new NetDataContractSerializer();

            XmlReader rdr = XmlReader.Create(inputStream);
            XmlDocument doc = new XmlDocument();
            doc.Load(rdr);

            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");
            foreach (XmlElement instanceElement in instances)
            {
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");
                XName key = (XName)DeserializeObject(s, keyElement);

                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");
                object value = DeserializeObject(s, valueElement);
                InstanceValue instVal = new InstanceValue(value);

                data.Add(key, instVal);
            }

            return data;
        }

        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)
        {
            object deserializedObject = null;

            MemoryStream stm = new MemoryStream();
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);
            element.WriteContentTo(wtr);
            wtr.Flush();
            stm.Position = 0;

            deserializedObject = serializer.Deserialize(stm);

            return deserializedObject;
        }

        //Saves the persistence data to an xml file.
        void Save(IDictionary<XName, InstanceValue> instanceData)
        {
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);
            XmlDocument doc = new XmlDocument();
            doc.LoadXml("<InstanceValues/>");

            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)
            {
                XmlElement newInstance = doc.CreateElement("InstanceValue");

                XmlElement newKey = SerializeObject("key", valPair.Key, doc);
                newInstance.AppendChild(newKey);

                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);
                newInstance.AppendChild(newValue);

                doc.DocumentElement.AppendChild(newInstance);
            }
            doc.Save(fileName);
       }

        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)
        {
            NetDataContractSerializer s = new NetDataContractSerializer();
            XmlElement newElement = doc.CreateElement(elementName);
            MemoryStream stm = new MemoryStream();

            s.Serialize(stm, o);
            stm.Position = 0;
            StreamReader rdr = new StreamReader(stm);
            newElement.InnerXml = rdr.ReadToEnd();

            return newElement;
        }
    }
}
```
